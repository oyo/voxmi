# voxmi

A minimalistic, zero dependency 3d engine for simple voxel visualizations based on WebGL.

[Sample Application](https://oyo.github.io/voxmi/)

![Sample Image](https://oyo.github.io/voxmi/sample-2.png)

## Usage (Typescript, vite and yarn)

    yarn create vite sample-voxmi --template vanilla-ts
    cd sample-voxmi
    yarn
    yarn add voxmi
    yarn dev
    # press o + Enter

You will see the Vite default app page. From there first
change `index.html` to remove any margins from the body:

```diff
- <body>
+ <body style="margin: 0; overflow: hidden;">
```

Then go and overwrite `src/main.ts` with this:

    import { Scene, SceneViewer } from 'voxmi'

    new SceneViewer(new Scene({ getData: () => [[[1, 0, 1]]] }))

In the browser you should now see a 3D rendering showing two cubes.

![Sample Image](https://oyo.github.io/voxmi/sample-1.png)

Now take this more sophisticated example:

    import {
      AnimatedScene,
      InterpolatedSurface,
      SceneViewer,
      Simple3D,
      UserInput,
    } from 'voxmi'

    new SceneViewer(
      new AnimatedScene(new InterpolatedSurface(100, 3, 1)).start(1000),
      new Simple3D(document.body).setPos({ z: -120 }).setCamFov(90),
      new UserInput().setMove({ u: 10, v: 5, w: -2 })
    )

You should see surface generated with cubic interpolation
similar to the sample application above.
