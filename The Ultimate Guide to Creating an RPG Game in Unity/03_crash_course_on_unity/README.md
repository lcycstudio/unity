## Section 03: Crash Course on Unity

#### Table of Contents

- Install Unity and Visual Studio 2022
- Unity windows and Tools
- Colliders and Rigibody
- Input and First script
- Move and Jump
- Serializefield
- Sprite sheet
- Animator
- Clean up
- Flip character
- 2D Collision Detection
- Jump animation
- Sticky walls
- Dash and timers
- Dash cooldown
- Attack animation
- Attack combo
- Inheritance
- Preparing inheritance
- Making enemy with Inheritance
- Enemy's attack
- End of crash course

### Install Unity and Visual Studio 2022

[Unity](https://unity.com/download)

[Visual Studio 2022](https://visualstudio.microsoft.com/)

#### Choose Components

- Game development with Unity

#### Visual Studio 2022

- Sign in

#### Launch Unity

- Projects
  - `New project`
  - Project name: `Rpg Udemy Course`
  - `Create Project`

#### Unity

- `Edit`
  - `Preferences`
    - `External Tools`
      - "Microsoft Visual Studio 2022"
    - `Generate Project Files`

### Unity windows and Tools

#### Window Tab

- `Window`
  - Layouts: "2 by 3"

![Layout](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/layout.png)

#### Square

- Right click `Sample Scene*`
  - 2D Objects
    - Sprites
      - Square

![Square](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/square.png)

#### Windows

- **Hierarchy Window**: see everything in the "scene".
- **Scene Window**: control objects in the scene
- **Game Window**: final cut of the rendered object in the game
- **Project Window**: navigate the files in the project
- **Inspector Window**: control panel for object's properties

#### Tools in Scene Window

- View Tool (hand)
  - Shortcut: **Q** or Wheel button on the mouse
- Move Toll (cross)
  - Shortcut: **W**
- Rotate Tool (circle)
  - Shortcut: **E**
- Scale Tool (arrow)
  - Shortcut: **R**
- Rect Tool (square)
  - Shortcut: **T**
- Transform Tool (complex)
  - Shortcut: **Y**

#### Duplicate Shortcut: Ctrl + D

#### Game Aspect

- Game Window
  - Free Aspect
    - 16:9 Aspect

#### Inspector Window

- `Transform`

  - Reset (the three dots on the right)
  - Position
  - Rotation
  - Scale

- `Sprite Renderer`

  - Sprite
  - Color
  - Flip
  - Draw Mode
  - Mask Interaction
  - Sprit Sort Point
  - Material
  - Additional Settings
    - Sorting Layer
    - Order in Layer

- `Add Component`

#### Project Window

Drag and drop "Warrior_Sheet-Effect.png" to it

[Warrior Sheet Effect](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/Warrior_Sheet-Effect.png)

#### C# Script

- Right Click Project Window
  - Create
    - C# Script: "Player"

### Colliders and Rigibody

- Make a square sprite and call it "Platform"
- Make a circle sprite and call it "Player"

#### Add Component

- Select Player

  - Add "Rigid Body 2D"
  - Add "Circle Collider 2D"
    - Edit Collider (optional)

- Select Platform

  - Add "Box Collider 2D"

#### 2D Physics Material

- Right click "Project Window"
  - Create
    - 2D
      - Physics Material 2D
        - Rename "My Material"
- Select Player
  - Rigid Body 2D
    - Material
      - Select "My Material"
    - Linear Drag: 0.5

![Colliders and Rigibody](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/colliders_and_rigibody.png)

### Input and First script

### Move and Jump

### Serializefield

### Sprite sheet

### Animator

### Clean up

### Flip character

### 2D Collision Detection

### Jump animation

### Sticky walls

### Dash and timers

### Dash cooldown

### Attack animation

### Attack combo

### Inheritance

### Preparing inheritance

### Making enemy with Inheritance

### Enemy's attack

### End of crash course
