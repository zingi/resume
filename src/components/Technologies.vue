<template>
  <h2>{{ t('technologies') }}</h2>
  <div id="logo-canvas"></div>
</template>

<script>
import Matter from 'matter-js'
import { onMounted } from '@vue/runtime-core'
import { useI18n } from 'vue-i18n'

export default {
  setup () {
    onMounted(() => {
      const viewportWidth = document.documentElement.clientWidth

      // module aliases
      const Engine = Matter.Engine
      const Render = Matter.Render
      const Runner = Matter.Runner
      const MouseConstraint = Matter.MouseConstraint
      const Mouse = Matter.Mouse
      const Composite = Matter.Composite
      const Bodies = Matter.Bodies

      // create engine
      const engine = Engine.create()
      const world = engine.world

      // set canvas width to screen width, if screen is smaller than 800
      const width = viewportWidth > 800 ? 800 : viewportWidth - 15
      // set height to a fraction of width
      const height = width * 0.6

      // get html element to insert canvas
      const canvas = document.querySelector('#logo-canvas')

      // create renderer
      const render = Render.create({
        element: canvas,
        engine: engine,
        options: {
          width,
          height,
          showAngleIndicator: false,
          showAxes: false,
          wireframes: false,
          background: 'transparent',
          wireframeBackground: 'transparent',
          pixelRatio: window.devicePixelRatio || 1
        }
      })

      Render.run(render)

      // create runner
      const runner = Runner.create()
      Runner.run(runner, engine)

      // add walls
      const wallThickness = 20.5
      const wallOffset = 0
      const wallOptions = {
        isStatic: true,
        render: {
          fillStyle: 'transparent'
        }
      }
      Composite.add(world, [
        // top
        Bodies.rectangle(width / 2, wallOffset, width + 0.5 + 2 * wallOffset, wallThickness, wallOptions),
        // bottom
        Bodies.rectangle(width / 2, height + wallOffset, width + 0.5 + 2 * wallOffset, wallThickness, wallOptions),
        // right
        Bodies.rectangle(width + wallOffset, height / 2, wallThickness, height + 0.5 + 2 * wallOffset, wallOptions),
        // left
        Bodies.rectangle(wallOffset, height / 2, wallThickness, height + 0.5 + 2 * wallOffset, wallOptions)
      ])

      // helper function, which returns random location in world area
      const getRandomSpawnLocation = () => {
        const minX = wallThickness
        const maxX = width - wallThickness
        const minY = wallThickness
        const maxY = height - wallThickness
        const deltaX = Math.abs(maxX - minX)
        const deltaY = Math.abs(maxY - minY)

        // generate random x and y
        const x = Math.round(minX + Math.random() * deltaX)
        const y = Math.round(minY + Math.random() * deltaY)

        return { x, y }
      }

      // size of rectangular bodies
      const rectWidth = width * 0.0875
      const rectHeight = rectWidth

      // radius of circular bodies
      const circleRadius = rectWidth / 2

      // x and y scale of texture
      const xScale = rectWidth * 0.009
      const yScale = rectHeight * 0.009

      // define rectangular icons
      const rectangularIcons = [
        { texture: require('../assets/icons/1Password.png'), xScale, yScale },
        { texture: require('../assets/icons/Affinity_Designer.png'), xScale, yScale },
        { texture: require('../assets/icons/Affinity_Photo.png'), xScale, yScale },
        { texture: require('../assets/icons/Alacritty.png'), xScale, yScale },
        { texture: require('../assets/icons/Chrome.png'), xScale, yScale },
        { texture: require('../assets/icons/Code.png'), xScale, yScale },
        { texture: require('../assets/icons/FinalCut.png'), xScale, yScale },
        { texture: require('../assets/icons/MSWD.png'), xScale, yScale },
        { texture: require('../assets/icons/Notion.png'), xScale, yScale },
        { texture: require('../assets/icons/PPT3.png'), xScale, yScale },
        { texture: require('../assets/icons/Safari.png'), xScale, yScale },
        { texture: require('../assets/icons/Slack.png'), xScale, yScale },
        { texture: require('../assets/icons/Tampermonkey.png'), xScale, yScale },
        { texture: require('../assets/icons/Threema.png'), xScale, yScale },
        { texture: require('../assets/icons/XCEL.png'), xScale, yScale },
        { texture: require('../assets/icons/clion.png'), xScale, yScale },
        { texture: require('../assets/icons/idea.png'), xScale, yScale },
        { texture: require('../assets/icons/Java.png'), xScale, yScale },
        { texture: require('../assets/icons/Discord.png'), xScale, yScale },
        { texture: require('../assets/icons/Element.png'), xScale, yScale },
        { texture: require('../assets/icons/Texpad.png'), xScale, yScale },
        { texture: require('../assets/icons/PostgreSQL.png'), xScale, yScale },
        { texture: require('../assets/icons/Typescript.png'), xScale, yScale },
        { texture: require('../assets/icons/Javascript.png'), xScale, yScale },
        { texture: require('../assets/icons/GitLab.png'), xScale, yScale },
        { texture: require('../assets/icons/VueJS.png'), xScale, yScale },
        { texture: require('../assets/icons/Trello.png'), xScale, yScale }
      ]

      // define circular icons
      const circularIcons = [
        { texture: require('../assets/icons/Firefox.png'), xScale, yScale },
        { texture: require('../assets/icons/MongoDB_Compass.png'), xScale, yScale },
        { texture: require('../assets/icons/Docker.png'), xScale, yScale },
        { texture: require('../assets/icons/GitKraken.png'), xScale, yScale },
        { texture: require('../assets/icons/Skype.png'), xScale, yScale },
        { texture: require('../assets/icons/qgis.png'), xScale, yScale },
        { texture: require('../assets/icons/Rust.png'), xScale, yScale },
        { texture: require('../assets/icons/Python.png'), xScale, yScale },
        { texture: require('../assets/icons/NPM.png'), xScale, yScale },
        { texture: require('../assets/icons/1Blocker.png'), xScale, yScale },
        { texture: require('../assets/icons/Insomnia.png'), xScale, yScale },
        { texture: require('../assets/icons/Octave.png'), xScale, yScale },
        { texture: require('../assets/icons/CARROTweather.png'), xScale, yScale },
        { texture: require('../assets/icons/Logic_Pro.png'), xScale, yScale },
        { texture: require('../assets/icons/Deno.png'), xScale, yScale },
        { texture: require('../assets/icons/SocketIO.png'), xScale, yScale },
        { texture: require('../assets/icons/GitHub.png'), xScale, yScale },
        { texture: require('../assets/icons/Jitsi_Meet.png'), xScale, yScale }
      ]

      // add recatngular icons to physics world
      for (const sprite of rectangularIcons) {
        const options = {
          render: {
            fillStyle: '#000000',
            strokeStyle: '#000000',
            sprite
          }
        }

        const { x, y } = getRandomSpawnLocation()
        Composite.add(world, [Bodies.rectangle(x, y, rectWidth, rectHeight, options)])
      }

      // add circular icons to physics world
      for (const sprite of circularIcons) {
        const options = {
          density: 0.0005,
          frictionAir: 0.06,
          restitution: 0.3,
          friction: 0.01,
          render: {
            sprite
          }
        }

        const { x, y } = getRandomSpawnLocation()
        Composite.add(world, [Bodies.circle(x, y, circleRadius, options)])
      }

      // add mouse control
      const mouse = Mouse.create(render.canvas)
      const mouseConstraint = MouseConstraint.create(engine, {
        mouse: mouse,
        constraint: {
          stiffness: 0.2,
          render: {
            visible: false
          }
        }
      })

      Composite.add(world, mouseConstraint)

      // keep the mouse in sync with rendering
      render.mouse = mouse

      // fit the render viewport to the scene
      Render.lookAt(render, {
        min: { x: 0, y: 0 },
        max: { x: width, y: height }
      })
    })

    const { t } = useI18n()
    return { t }
  }
}
</script>
