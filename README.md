# brackeys-godot-3d
I wanted to follow along Brackey's latest video and experiment with 3D game development in Godot

## 3D Physics Engine
**Brackey's suggested** to use the Jolt Engine, I went ahead and installed it via the Asset Library. Apparently Jolt will ship with Godot 4.4 out of the box, so I can update this project later when Godot 4.4 releases it's first stable version.

## 3D Editor, Navigation and Tools
I learned a bit about using the transformation section on the right to edit 3d nodes. The gizmo's are also really useful for this.

Some default shortcuts to be aware of:
 - Q : Select Mode
 - W : Move Mode
 - E : Rotate Mode
 - R : Scale Mode

Hold `Ctrl` while using these to enable snapping. Also pressing `T` will toggle between local mode and global mode. This will update the orientation of your gizmos.

**Brackey's suggested** adding a custom shortcut. Under Editor -> Editor Settings -> Shortcuts -> Begin Rotate Transformation. I bound this to `Shift + R`. This will start a rotation transformation that follows the mouse, and if you type `X`, `Y`, or `Z`, it will lock this rotation to the corresponding axis.

## Prototype with Greyboxing
It is so essential to start out with prototypes for our levels, to avoid wasting time bogged down in the details when our idea is not concrete yet.

When ready to start replacing your Greyboxing with actual assets, you can set all the greyboxes as collision disabled, and set the color for them to something easy to see like a magenta, also set the transparency to alpha, and make them a bit transparent. This will make it easier to put your assets in place.

**Brackey's suggests** Using snapping when prototyping, and he also updated his snap settings. Transform -> Configure Snap
![Snap Settings](readme_screenshots/snap_settings.png)

Godot makes this very quick and easy through the use of CSG nodes (Constructive Solid Geometry). CSG nodes have little handles which can be used to quickly scale your nodes. If you hold `Alt` while dragging these handles, it will mirror on both sides. Collision can also be quickly enabled by checking the box `Use Collision`

We can also do cool things like subtract one CSG node from another, by creating a CSG node that is a child of the other node, and changing the Operation. This can be an easy way to create doors, windows, etc...

## 3D Rigs and Animation
There are a few different way 3D animated rigs can be bundled in glb files.
 - All in one, where the glb contains the mesh, the animations, and the animation player. See the [Skeleton model](brackeys-3d/models/skeleton).
 - Separate glb files for the mesh, and each animation. See the [Zombie model](brackeys-3d/models/zombie).

**Brackey's suggests** Using the separate files method, that way you don't need to include all the extra animations that you might not be using.

Protip, looping of imported animations can be set on the advanced import screen.

## Environment and Lighting

### Environment
We are reviewing the different types of environments we can set. There are a few proceduraly generated options.

We can also set the background to an HDRI, a good website to find freely licenses HDRI's is [Poly Haven](https://polyhaven.com/hdris).

No matter which background we choose, we can adjust the instensity with the energy multiplier.

Be careful about importing HDR files, as the initial import process can be a bit graphics intensive. Make sure you have a decent size VRAM on your graphics card before doing this. Otherwise you might find godot freezing up on you during import.

Some things to try:
 - Enable SSAO, (or Screen Space Ambient Occlusion) will shadow areas where light might have a hard time reaching.
 - Tonemap can be configured for the overall style of the game. Try using ACES, with exposure of 1.2, and white of 6. The exposure helps to brighten up the scene.
 - Select Adjustments -> Color Correction, Gradient Texture 1D, Add two more points near the white and black point, we can use them to bring in warmth in the highlights, make the shadows cooler, and adjust the contrast moving them back and forth.

### Lighting
We added some omni directional lights to the scene. Some cool features for lights is to do things like:
 - Enable Shadows, although be cautious not to do this too much.
 - Play with the range of the lights if we want it to light more or less of the area.

### Camera Settings
Things to try:
 - Change `Projection` to Orthogonal, adjust the size to fit. This will be useful for an isometric game.
 - In perspective mode we can adjust the FOV (Field of View)
 - We can adjust camera attributes, either directly for one camera, or in the world environment for all cameras.

## Rendering Settings
Check out these project settings areas with Advanced Settigns enabled:
 - Rendering -> AntiAliasing, Brackey's enabled 4x Slow
 - Rendering -> Light and Shadows
 - Rendering -> Environment
