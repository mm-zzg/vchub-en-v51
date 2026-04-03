# Lighting Settings

When creating a new 3D scene, the system includes a default ambient light and a parallel light. However, the default settings may not effectively highlight model details, resulting in a generally dark appearance with limited contrast.

To achieve better visual effects, you can optimize lighting by adding and adjusting multiple light sources.

## Adjusting Default Lights

After creating a new scene, it is recommended to first adjust the default parallel light:

1. **Position**: Place it directly above the model with `X = 0`, `Z = 0`, and increase `Y` appropriately based on the model's height.
2. **Light Intensity**: Set to **2** to enhance the top-down lighting effect.

## Adding Custom Lights

**Scene Example**: By adding multiple parallel lights, you can simulate a more realistic lighting environment, thereby enhancing contrast and the sense of depth in the model.

**Steps:**

1. After adjusting the default directional light, add **three additional parallel lights**: **Parallel Light 2**, **Parallel Light 3**, and **Parallel Light 4**.

2. Parallel Light 2 – *Key Light (Main Light Source)*

     a. **Position**: Lower right side of the scene, slightly centered.

     b. **Intensity**: Recommended to set **4 or higher** (example: **7**).
   
     c. **Purpose**: Provides the main lighting direction, creating a clear light–dark contrast.

3. Parallel Light 3 – *Fill Light (Secondary Light Source)*

     a. **Position**: Diagonally opposite the key light, slightly lower in height.
   
     b. **Intensity**: Recommended to set **below 1** (example: **0.5**).
   
     c. **Purpose**: Softens the model’s shadowed areas, creating smoother light transitions.
     
4. Parallel Light 4 – *Balance Light*

     a. **Position**: Upper left side, slightly lower than the key light.

     b. **Intensity**: Can remain at the default value (e.g., **1**).

     c. **Purpose**: Further balances overall lighting, preventing excessive darkness in some areas.


| **Before adding lights**  | **After adding lights**   |
|---------------------------|---------------------------|
| ![alt text](3d_LSettings1.png) | ![alt text](3d_LSettings2.png) |

## Usage Recommendations and Notes

- **Number of Lights**: It is recommended to keep the total number of light sources **≤ 50** to avoid performance issues or scene lag.
- **Direction and Intensity Adjustments** ：After adding lights, you must manually adjust their direction and intensity to achieve the desired effect.
- **Skybox Influence**: Enabling a skybox may affect the overall lighting ambiance. You should adjust the light intensity accordingly based on the actual visual effect.

By configuring lighting properly, you can significantly enhance the visual appearance of models in the 3D scene—achieving a more natural balance of light and shadow as well as spatial depth.

Users are encouraged to flexibly adjust the type, position, and intensity of light sources based on their specific scene requirements to achieve the best visual outcome.