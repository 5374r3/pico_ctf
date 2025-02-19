1️⃣ School Coordinate System (Cartesian Plane)

In mathematics, you learned about the Cartesian coordinate system, which looks like this:

```css
      ↑ +y
      |
 -x   |   +x
←------0------→
      |
      ↓ -y
```

- The **origin (0,0)** is in the **center**.
- The **x-axis** increases to the **right** and decreases to the **left**.
- The **y-axis** increases **upward** and decreases **downward**.

For example:

- **(2,3) is 2 steps right, 3 steps up.**
- **(-4,-2) is 4 steps left, 2 steps down.**

2️⃣ Computer Graphics Coordinate System

In computer graphics (C++, OpenGL, SDL, etc.), the coordinate system is different from what you learned in school.

✅ The origin (0,0) is at the top-left corner!
✅ The x-axis increases to the right (same as school).
✅ The y-axis increases downward (opposite of school).

```css
(0,0) ───► +x
   |       
   ▼
  +y
```

So, in a **computer screen or game grid**:

- **(0,0) is the top-left corner** of the screen.
- **(5,10) means 5 pixels to the right, 10 pixels down.**
- **(100,50) means 100 pixels right, 50 pixels down.**

📌 **Example: 5x5 grid (used in games)**  
If you were designing a small **game map**, it would look like this:


|y\x|0|1|2|3|4|
|---|---|---|---|---|---|
|**0**|(0,0)|(1,0)|(2,0)|(3,0)|(4,0)|
|**1**|(0,1)|(1,1)|(2,1)|(3,1)|(4,1)|
|**2**|(0,2)|(1,2)|(2,2)|(3,2)|(4,2)|
|**3**|(0,3)|(1,3)|(2,3)|(3,3)|(4,3)|
|**4**|(0,4)|(1,4)|(2,4)|(3,4)|(4,4)|

- The **x-axis increases** ➡️ (right).
- The **y-axis increases** ⬇️ (down).

## **2️⃣ Negative Coordinate Example (Computer Graphics)**

In **computer graphics (games, UI, etc.),** negative coordinates usually **go off-screen** (outside the drawable area). 
Example:

| y\x    | -2  | -1  | 0        | 1   | 2   |
| ------ | --- | --- | -------- | --- | --- |
| **-2** | ❌   | ❌   | ❌        | ❌   | ❌   |
| **-1** | ❌   | ❌   | ❌        | ❌   | ❌   |
| **0**  | ❌   | ❌   | 🟢 (0,0) | ✔️  | ✔️  |
| **1**  | ❌   | ❌   | ✔️       | ✔️  | ✔️  |
| **2**  | ❌   | ❌   | ✔️       | ✔️  | ✔️  |
- Cells marked ❌ **don’t exist** on a typical computer screen.
- Cells marked ✔️ **are inside the valid screen area**.
- The 🟢 represents the **origin (0,0) in screen coordinates**.