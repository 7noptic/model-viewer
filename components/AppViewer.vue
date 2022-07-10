<template>
  <div ref="canvas" style="z-index: 1" />
</template>

<script>
import * as THREE from 'three'
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader'
import { DRACOLoader } from 'three/examples/jsm/loaders/DRACOLoader'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js'
import { RGBELoader } from 'three/examples/jsm/loaders/RGBELoader'
import { PMREMGenerator } from 'three'

export default {
  name: 'TheCanvas',
  layout: 'none',
  props: {
    // person: {
    //   type: Object,
    //   required: true
    // },
    filesProps: {
      type: Array,
      required: false,
      default: []
    }
  },
  data () {
    const scene = new THREE.Scene()
    const camera = new THREE.PerspectiveCamera(
      75,
      window.innerWidth / window.innerHeight,
      0.1,
      500
    )
    const renderer = new THREE.WebGLRenderer({
      antialias: true,
      alpha: true
    })

    const pmremGenerator = new PMREMGenerator(renderer)
    pmremGenerator.compileEquirectangularShader()

    const ambientLight = new THREE.AmbientLight('#404040', 1)
    const pointLight = new THREE.PointLight('#ff6800', 1)
    const pointLightFront = new THREE.PointLight('#ffd3ce', 0.6)

    const filesData = ['/models/BODY/COSSACK_BODY_1#100.glb']
    return {
      scene,
      camera,
      controls: [],
      renderer,
      ambientLight,
      pointLight,
      pointLightFront,
      speed: 0.01,
      filesData,
      pmremGenerator
    }
  },
  computed: {
    files () {
      return ['/models/BODY/COSSACK_BODY_1#100.glb', ...this.filesProps]
    },
    rotate () {
      if (this.speed === '') {
        return 0
      } else {
        return this.speed
      }
    }
  },
  watch: {
    files: {
      handler (newVal, oldVal) {
        this.start()
        console.log(this.files)
      }
    }
  },
  mounted () {
    this.start()
  },
  methods: {
    stop () {
      cancelAnimationFrame(this.id)// Stop the animation
      this.renderer.domElement.addEventListener('dblclick', null, false) //remove listener to render
      this.scene = null
      this.projector = null
      this.camera = null
      this.controls = null
    },
    start () {
      this.ambientLight.position.set(0, 100, 0)
      this.pointLight.position.set(0, 7, -15)
      this.pointLightFront.position.set(0, 7, 15)
      this.scene.add(this.camera)
      this.scene.add(this.ambientLight)
      this.scene.add(this.pointLight)
      this.scene.add(this.pointLightFront)
      this.scene.fog = new THREE.Fog('#fff', 0.015, 100)
      const dracoLoader = new DRACOLoader()
      dracoLoader.setDecoderPath('https://raw.githubusercontent.com/mrdoob/three.js/dev/examples/js/libs/draco/') // use a full url path
      const loader = new GLTFLoader()
      loader.setDRACOLoader(dracoLoader)
      for (const file of this.files) {
        loader.load(encodeURIComponent(file), (object) => {
          console.log('LOADED', object)
          object.scene.position.set(0, -6.5, 0)
          this.scene.add(object.scene)
        })
      }

      this.renderer.setSize(window.innerWidth, window.innerHeight)

      this.getCubeMapTexture('/model-viewer/2k.hdr').then(({ envMap }) => {
        this.scene.environment = envMap
        // this.scene.background = this.state.background ? envMap : null;
      })

      this.camera.position.z = 8.3
      this.camera.position.y = 2.5
      this.camera.position.x = 3.5
      this.controls = new OrbitControls(this.camera, this.renderer.domElement)
      this.controls.enableZoom = false
      this.$refs.canvas.appendChild(this.renderer.domElement)
      this.animate()
    },
    getCubeMapTexture (path) {
      return new Promise((resolve, reject) => {
        new RGBELoader()
          .load(path, (texture) => {
            const envMap = this.pmremGenerator.fromEquirectangular(texture).texture
            this.pmremGenerator.dispose()
            resolve({ envMap })
          }, undefined, reject)
      })
    },
    animate () {
      if (this.controls) {
        requestAnimationFrame(this.animate)
        this.renderer.render(this.scene, this.camera)
        this.controls.update()
      }
    }
  }
}
</script>
<style>
canvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 1;
}
</style>
