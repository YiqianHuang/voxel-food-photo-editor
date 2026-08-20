# Voxel Food Photo Editor

Turn supplied food and drink photographs into reality-versus-voxel edits: only the edible contents become recognizable, block-built voxel versions of themselves. Everything else remains photorealistic.

## What it preserves

- The actual dish or drink: its count, shape, layers, toppings, colours, placement, and perspective.
- People, hands, clothing, tableware, packaging, furniture, environment, lighting, shadows, and camera composition.

By default, plates, bowls, cups, glasses, chopsticks, cutlery, trays, wrappers, and napkins remain real. The voxel edit applies only to food and drink contents.

## Optional food + vessels mode

Enable this mode only when the user explicitly says **“餐具也游戏化”**. In that case, edible contents **and their directly associated containers/tableware** may be rebuilt as voxel objects. Without that explicit request, keep every vessel and utensil photorealistic.

## Examples

### Burgers and fries

| Before preprocessing | Food-only voxel edit |
| --- | --- |
| ![Burgers and fries before](examples/03-burgers-fries-preprocessed.jpg) | ![Burgers and fries with only the food voxelized](examples/03-burgers-fries-voxel.png) |

### Multi-dish meal

| Before preprocessing | Food-only voxel edit |
| --- | --- |
| ![Multi-dish meal before](examples/2019-03-08-132320-preprocessed.jpg) | ![Multi-dish meal with only the food voxelized](examples/2019-03-08-132320-voxel.png) |

## Use

Ask Codex to use `$voxel-food-photo-editor` with one or more food photographs. It processes every readable image supplied, saving a restrained preprocessed copy and one final voxel edit per image.

## License

This skill and the included examples are available for personal, non-commercial use only. See [LICENSE](LICENSE).
