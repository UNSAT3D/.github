# Project log


## Continue here

Newer entries above.

## 2023-08-08. Change of roles

As of today:

- Aron is the lead engineer of this project.
- Pablo R. is just another engineer.

We did this in order to ensure Aron can lead one project and Pablo R. doesn't have to lead two.

## 2023-07-22. Data decisions

Hongyang mailed us their decisions on what data to prepare:
- 2D:
	- randomize: saturation degree, particule configuration
	- particle size distribution modelled after X-ray images
	- Not sure how many
- 3D:
	- Sub-volumes cropped from X-ray images
	- particles approximated as spheres with radii such that volume is preserved.
	- Aim for around 10

Plan:
1. Try 2D UNet on 2D data
2. Try 2D UNet on slides of 3D data
3. ? train 3D Unet

source of UNets: https://paperswithcode.com/method/u-net

## 2023-07-19. Data inspection meeting

- Location: Amsterdam
- Present: 
	- Pablo Rodríguez
	- Aron Jansen
	- Floriana Anselmucci
	- Hongyang Cheng 
	- Sherrin Joseph (online)

This was the first meeting involving the whole team. Although the official purpose of it was to take a look at the data together, it also had the obvious social component of getting to know each other.

Regarding the data, in preparation of the meeting Aron and Pablo R. created the [data](https://github.com/UNSAT3D/data) and [sandbox](https://github.com/UNSAT3D/sandbox) repositories. The data-related issues were discussed in the form of GitHub issues on the [data](https://github.com/UNSAT3D/data) repository, specifically:

- [Missing data](https://github.com/UNSAT3D/data/issues/1)
- [We don't have labeled data](https://github.com/UNSAT3D/data/issues/2)
- [Simulation and experimental data look very different](https://github.com/UNSAT3D/data/issues/3)
- [Figure out how much data should be generated](https://github.com/UNSAT3D/data/issues/4)

All the issues were closed after the meeting.

### Roots

We may need to subset the plant roots out of the images. The color histogram cannot discriminate them from water (although Floriana did [some work](https://github.com/FloAns/Rooted_Soil-Tomograph_Image-Processing) on this), plus the synthetic data has no roots on it. Additionally, roots affect water suction.

### Label classes

The current labels are just three:

- Solid
- Air
- Water

### Filenames

The naming structure follows the following pattern:

```
{type of sand}Sand_Day{number}Growth.tif
```

where:

- `type of sand` can be `Coarse` or `Fine`.
- `number`: is the number of days the plant was allowed to grow. There was no watering in between.

We'll train for sure using coarse sand. Fine sand will probably cause us problems due to the image resolution.

### More data?

We will have more simulations in the near future. Each of them takes around 12 hours to complete. We'll need multiple simulations with different saturation degrees. It is also possible to run a simulation based on an experimentally measured geometry.

Floriana has additional experimental data, labeled, only for coarse sand. We can use this as a plan B if synthetic data fails us.

> [!info] Why not use her algorithm?
> Floriana has automatically labeled data, why do we want a neural network instead?
> Simply because the algorithm she used is very costly.

Last but not least, we can always use simulated data to predict simulated data, as a backup plan.

### Expected contributions

| Contributor | Activity                    |
|-------------|-----------------------------|
| Floriana    | Experiments                 |
| Hongyang    | Simulations and supervision |
| Sherrin     | Simulations                 |
| Aron        | UNET                        |
| Pablo R.    | UNET and coordination       |

### Loose comments

- Fine sand causes higher water columns
- Classical image analysis fails at certain saturation values
- Changing `github` to `githubtocolab` in the github url opens a Google colab doc.

### Glossary

- **REV**: Representative Element Volume
- **Suction**: pressure difference along an interface.
- **Wetting**: how hydrophobic/hydrophilic a solid is.

### Action points

- [ ] Aron will search for pretrained networks for similar 3D problems
- [ ] Plan a kickoff meeting with Rena Bakhshi
	- Should happen between mid September and October
	- The project will start in mid October

## 2023-06-21

- Created the [project organization](https://github.com/UNSAT3D)
- Created some repositories:
    - [data](https://github.com/UNSAT3D/sandbox)
    - [sandbox](https://github.com/UNSAT3D/sandbox)
- Took a first look at the data and found the following [issues](https://github.com/UNSAT3D/data/issues) to be discussed in our upcoming meeting

## 2023-06-09

- The project's engineers are officially introduced:
    - Pablo Rodríguez-Sánchez (lead)
    - Aron Jansen
    
## 2023-03-01

- Official start date
    - Postponed to 2023-10-01
