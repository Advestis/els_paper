## Stress Testing Electrical Grids: Generative Adversarial Networks For Load Scenario Generation<br><sub>Official GitHub repository for the Elsevier Energy and AI paper</sub>

![Graphical abstract](https://github.com/Advestis/els_paper/blob/master/graphical_abstract.png)

**Stress Testing Electrical Grids: Generative Adversarial Networks For Load Scenario Generation**<br>
Matteo Rizzato, Nicolas Morizet, William Maréchal and Christophe Geissler<br>
DOI: https://doi.org/10.1016/j.egyai.2022.100177<br>

**Abstract**: *As the energy transition is upon us, the replacement of combustion engines by electrical ones will imply a greater stress on the electrical grid of different countries. Therefore, it is of paramount importance to simulate a great number of hypothetical multi-variant scenarios to correctly plan the roll-out of new grids. In this paper, we deploy Generative Adversarial Networks (GANs) to swiftly reproduce the non-Gaussian and multimodal distribution of real energy-related samples, making GANs a valuable tool for data generation in the field. In particular, we propose an original dataset deriving from the aggregation of two European providers including hourly electric inland generation from several European countries. This dataset also comes along with the corresponding season, day of the week, hour of the day and macro-economic variables aiming at unequivocally describing the country's energetic profile. Finally, we evaluate the performance of our model via dedicated metrics capable of grasping the non-Gaussian nature of the data and compare it with the state-of-the-art model for tabular data generation.*

**Dataset**: https://storage.googleapis.com/neg_dataset_eu/data_set.csv

**Proposed Model**: https://storage.googleapis.com/els-models/proposed_GAN_model.zip

## Release notes


## Requirements
- Tensorflow 2.3.2
- Matplotlib 3.4.1
- GetDist 1.2.2
- Pandas
- Numpy

## Getting started

## Citation
```
@article{RIZZATO2022100177,
  author = {Matteo Rizzato and Nicolas Morizet and William Maréchal and Christophe Geissler},
  title = {Stress testing electrical grids: Generative Adversarial Networks for load scenario generation},
  journal = {Energy and AI},
  pages = {100177},
  year = {2022},
  issn = {2666-5468},
  doi = {https://doi.org/10.1016/j.egyai.2022.100177},
  url = {https://www.sciencedirect.com/science/article/pii/S2666546822000295},
  keywords = {Generative Adversarial Networks, Artificial data, Electrical grid, Simulation, Load profiles}
}
```
