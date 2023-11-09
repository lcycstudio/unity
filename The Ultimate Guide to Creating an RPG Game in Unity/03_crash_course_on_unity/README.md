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

![Layout](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/layout.png)

#### Square

- Right click `Sample Scene*`
  - 2D Objects
    - Sprites
      - Square

![Square](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/square.png)

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

[Warrior Sheet Effect](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/Warrior_Sheet-Effect.png)

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

![Colliders and Rigibody](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/colliders_and_rigibody.png)

### Input and First script

There are an old input system and a new input system.

#### Script

- Project Window
  - Drag Player script to Player object
    - Edit the script

![Visual Studio 2022 - Player Script](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/visual_studio_2022.png)

```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class NewBehaviourScript : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        Debug.Log("Start was called.");
    }

    // Update is called once per frame
    void Update()
    {
        Debug.Log("Update is called.");
    }
}
```

#### Console Window

- Window
  - General
    - Console
      - `Collapse`

#### Input Keys

- GetKey
- GetKeyDown
- GetKeyUp

```cs
void Update()
{
    if (Input.GetKey(KeyCode.Space))
    {
        Debug.Log("You holding the space button!");
    }
    if (Input.GetKeyDown(KeyCode.Space))
    {
        Debug.Log("You pressed space button");
    }
    if (Input.GetKeyUp(KeyCode.Space))
    {
        Debug.Log("You released space button!");
    }
}
```

![Input Keys](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/input_keys.png)

Unity Key Codes (https://docs.unity3d.com/ScriptReference/KeyCode.html)

#### Input Buttons

```cs
if (Input.GetButtonDown("Jump"))
{
    Debug.Log("Jump");
}
```

#### Jump Button

- Edit
  - Project Settings
    - Input Manager
      - Axes
        - Jump
          - Name: Jump
          - Positive Button: space

#### Axes

```cs
void Update()
{
    // decimal pixel movement
    Debug.Log(Input.GetAxis("Horizontal"));

    // integer pixel movement
    Debug.Log(Input.GetAxisRaw("Horizontal"));
}
```

#### Input Variable xInput

```cs
public class Player : MonoBehaviour
{
    public float xInput;

    // Start is called before the first frame update
    void Start()
    {
        Debug.Log("Start was called.");
    }

    // Update is called once per frame
    void Update()
    {
        xInput = Input.GetAxisRaw("Horizontal");
        Debug.Log(xInput);
    }
}
```

![GetAxisRaw](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/getAxisRaw.png)

### Move and Jump

#### Public and Private

**Public**

- you can see the variable / value in the inspector

**Private**

- you cannot see the variable / value in the inspector
- you cannot access this variable / value from another script

#### Create RigidBody2D variable

```cs
public Rigidbody2D rb;
```

- Inspector
  - Drag the RigidBody 2D to Rb
  - Variable `rb` is the same as the RigidBody 2D in the Inspector

```cs
void Start()
{
    // Push our ball to the right side
    rb.velocity = new Vector2(5, rb.velocity.y);
    Debug.Log("Start was called.");
}
```

![RigidBody2D](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/RigidBody2D.png)

### SerializeField

SerializeField is one that makes variables accessible to Unity.

```cs
private Rigidbody2D rb;

[SerializeField] private float moveSpeed;
[SerializeField] private float jumpForce;


public float xInput;

// Start is called before the first frame update
void Start()
{
    rb = GetComponent<Rigidbody2D>();
}
```

The above `rb` still uses RigidBody2D but it is shown in the debug mode of the Inspector window, not the normal mode.

![Debug Mode](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/debug_mode.png)

### Sprite sheet

#### Cutting sprite sheet

- Project window
  - Warrior_Sheet-Effect.png
    - Inspector window
      - Sprite Mode: Multiple
      - `Sprite Editor`

![Sprite Inspector](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/sprite_inspector.png)

#### Sprite Editor

![Sprite Editor](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/sprite_editor.png)

- Slice Editor
  - Slice
    - Type: Grid By Cell Size
    - Pixel Size
      - X: 69
      - Y: 44
    - Slice
    - Apply

![Sliced Sprite Sheet](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/sliced_sprite_sheet.png)

- Drag sprite sheet to Scene window

  - Select Warrior_Sheet-Effect.png
    - Inspector Window
      - Sprite Mode
        - Pixels Per Unit: 16
        - Apply
      - Advanced
        - Filter Mode: Point (no filter)
        - Compression: None

- Delete object "Warrior_Sheet-Effect_0"
- Drag sprite "Warrior_Sheet-Effect_0" to Player Sprite Renderer
- Sprite Renderer
  - Sprite: Warrior_Sheet-Effect_0
  - Color: Transparent

#### Center Point of Sprite Sheet

- Hierarchy Window
- Right Click "Player"
  - Create Empty
    - Name: Animator
- Player
  - Sprite Renderer
    - Remove Component
- Animator
  - Add Component
    - Sprite Renderer
      - Drag Warrior_Sheet-Effect_0 to Sprite
- Animator (Child Object)
  - Transform
    - X: 0.4
- Player
  - Scene Window
    - Choose "Pivot"
  - Circle Collider 2D
    - Remove Component
  - Add Component
    - Capsule Collider 2D
      - Edit Collider
  - RigidBody 2D
    - Costraints
      - Freeze Rotation: Z
    - Collision Detection: Continuous
    - Interpolate: Interpolate

![Warrior_Sheet-Effect_0](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/Warrior_Sheet-Effect_0.png)

### Idle Animator

- Window
  - Animation
    - Animation
  - Animation
    - Animator

Animator takes a number of sprites and place them in a certain order to make it an animation.

- Project window
  - Right click
    - Create
      - Animator Controller
      - Name: "Player_AC"
- Drag Player_AC to Animator
- Select Animation Window
  - Create
    - playerIdle.anim
- Project window
  - Drag the first 6 sprite sheets of Idle to Animation window
  - Show Sample Rate
    - Samples: 10

![Animation Window](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/animation_window.png)

#### Move Animator

- Hierarchy window
  - Animator
    - Animation window
      - playerIdle
        - Create New Clip
          - playerMove.anim
      - playerMove
        - Project window
          - Drag move spirtes to Animation window
          - Samples: 10
- Play

![Animator Window](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/animator_window.png)

#### Transition Move

- Animator Window
  - Parameters
    - "+"
      - Bool
        - "isMoving"
  - Base Layer
    - Right click "playerIdle"
      - Make transition
        - playerMove
    - Select the arrow line
      - Inspector window
        - Conditions
          - "+"
            - isMoving: true
    - Right click "playerMove"
      - Make transition
        - playerIdle
    - Select the upward arrow line
      - Inspector window
        - Conditions
          - "+"
            - isMoving: false
- Player
  - Inspector window
    - Player (Script)
      - Open the script
      - `public Animator anim;`
  - Drag Animator to "Anim" under Player (Script)

Player doesn't have any animator. The child component, Animator, has the animator.

#### Smooth Transition

- Animator window

  - Downward arrow line

    - Inspector window
      - Has Exit Time: uncheck
      - Settings
        - Transition Duration: 0

  - Upward arrow line
    - Inspector window
      - Has Exit Time: uncheck
        - Settings
        - Transition Duration: 0

![Smooth Transition](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/smoot_transition.png)

### Clean up

Alt + Arrow Down Key

- Select `rb.velocity = new Vector2(rb.velocity.x, jumpForce);`
- Alt + Enter
- Extract Method
- Enter

![Clean Up](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/clean_up.png)

### Flip character

```cs
...
private int facingDir = 1;
private bool facingRight = true;
...

void Update()
{
    ...
    FlipController();
    ...
}

...

private void Flip()
{
    facingDir = facingDir * -1;
    facingRight = !facingRight;
    transform.Rotate(0, 180, 0);
}

private void FlipController()
{
    if (rb.velocity.x > 0 && !facingRight) Flip();

    else if (rb.velocity.x < 0 && facingRight) Flip();
}
```

### 2D Collision Detection

```cs
[Header("Collision Info")]
[SerializeField] private float groundCheckDistance;
[SerializeField] private LayerMask whatIsGround;
private bool isGrounded;

void Update()
{
    ...
    CollisionChecks();
    ...
}

private void CollisionChecks()
{
    isGrounded = Physics2D.Raycast(transform.position, Vector2.down, groundCheckDistance, whatIsGround);
}
```

- Player

  - Inspector window
    - Player (Script)
      - Ground Check Distance: 1.4
    - Layer
      - Add Layer
        - User Layer 3: Ground

- Select Platform & Platform (1)

  - Inspector window
    - Layer: Ground

- Player
  - Inspector
    - Player (Script)
      - What Is Ground: Ground

### Jump animation

#### Player Jump

- Hierarchy Window
  - Animator
    - Animation Window
      - Create New Clip
        - Animations Folder: playerJump.anim
          - Project window
            - Graphics
              - Warrior_Sheet-Effect: 41, 42, 43
                - Drag them to Animation window
                  - Samples: 10
- Animator window
  - Any State
    - Make transitions to playerJump
      - "+"
        - Bool: isGrounded
          - Select downward arrow line
            - Inspector
              - Conditions
                - List is Empty: "+"
                  - isGrounded: false
              - Settings
                - Transition Duration: 0
                - Can Transition To Self: uncheck
- Animator window
  - Select playerJump
    - Make transitions to playerIdle
      - Select arrow line
        - Inspector
          - Conditions
            - isGrounded: true
          - Has Exit Time: uncheck
          - Settings
            - Transition Duration: 0

#### Player Fall

- Hierarchy window

  - Animator
    - Animation window
      - Create New Clip
        - Animations folder: playerFall.anim
          - Project window
            - Graphics
              - Warrior_Sheet-Effect: 46, 47, 48
                - Drag them to Animation window
                  - Samples: 10

- Animator window
  - Right click
    - Create State
      - From New Blend Tree
        - Inspector
          - Name: Jump/Fall
            - Animator window:
              - Double click Jump/Fall
                - Inspector
                  - Motion: "+"
                    - Add Motion Field
                    - Add Motion Field
                  - Automate Threshold: uncheck
                  - playerFall
                    - Thres: -1
              - Parameters:
                - Rename "Blend" to "yVelocity"
    - Select Blend Tree
      - Inspector window
        - Drag "Blend Tree" Tab upward

```cs
private void AnimatorControllers()
{
    bool isMoving = rb.velocity.x != 0;

    anim.SetFloat("yVelocity", rb.velocity.y);
    anim.SetBool("isMoving", isMoving);
    anim.SetBool("isGrounded", isGrounded);
}
```

![Blend Tree](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/blend_tree.png)

- Animator window
  - Delete `playerJump` and `playerFall` states
  - Select `Any State`
    - Make transition to `Jump/Fall`
      - Select arrow line
        - Inspector
          - Conditions: "+"
            - isGrounded: false
          - Settings
            - Transition Duration: 0
            - Can Transition To Self: uncheck
  - Select `Jump/Fall`
    - Make transition to `playerIdle`
      - Select arrow line
        - Inspector
          - Conditions: "+"
            - isGrounded: true
          - Settings:
            - Has Exit Time: uncheck
            - Transition Duration: 0

![Jump/Fall](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/jump_fall.png)

- Player
  - RigidBody 2D
    - Gravity: 3.5
  - Player (Script)
    - Jump Force: 12
    - Move Speed: 6

### Sticky walls

- Project window

  - Right click
    - Create
      - 2D
        - Physics Material 2D
          - Name: SlippyMat
          - Inspector
            - Friction: 0
    - Create
      - Folder
        - Materials
          - Drag SlippyMat to Materials folder

- Hierarchy window
  - Player
    - Inspector window
      - Rigidbody 2D
        - Material: SlippyMat

### Dash and timers

#### Time.DeltaTime

It shows you time that passed between frames and we can use it as a timer for cooldown or something else.

```cs
[Header("Dash Info")]
[SerializeField] private float dashSpeed;
[SerializeField] private float dashDuration;
[SerializeField] private float dashTime;
...
private void Movement()
{
    if (dashTime > 0)
    {
        rb.velocity = new Vector2(xInput * dashSpeed, 0);
    }
    else
    {
        rb.velocity = new Vector2(xInput * moveSpeed, rb.velocity.y);
    }
}
```

- Hierarchy window
  - Player
    - Inspector
      - Player (Scripts)
        - Dash Info
          - Dash Speed: 15
          - Dash Duration: 0.5
  - Main Camera
    - Inspector
      - Camera
        - Size: 8

#### Dash Animation

- Hierarchy window

  - Animator
    - Animation window
      - Create New Clip
        - Animations folder: playerDash
          - Project window
            - Graphics folder
              - Warrior_Sheet-Effect: 69 - 72
                - Drag them to Animation window
                - Samples: 10

- Animator window
  - Make transition from `Any State` to `playerDash`
    - "+"
      - Bool: isDashing
    - Select arrow line
      - Conditions:
        - isDashing: true
      - Settings:
        - Transition Duration: 0
        - Can Transition To Self: uncheck
  - Make transtion from `playerDash` to `playerIdle`
    - Select arrow line
      - Conditions:
        - isDashing: false
      - Settings:
        - Transition Duration: 0
        - Has Exit Time: uncheck

![Player Dash](/The%20Ultimate%20Guide%20to%20Creating%20an%20RPG%20Game%20in%20Unity/03_crash_course_on_unity/images/player_dash.png)

```cs
private void AnimatorControllers()
{
    ...
    anim.SetBool("isDashing", dashTime > 0);
}
```

- Hierarchy
  - Player
    - Player (Script)
      - Move Speed: 6
      - Jump Force: 12
      - Dash Speed: 15
      - Dash Duration: 0.25

### Dash cooldown

### Attack animation

### Attack combo

### Inheritance

### Preparing inheritance

### Making enemy with Inheritance

### Enemy's attack

### End of crash course
