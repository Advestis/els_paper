## Stress Testing Electrical Grids: Generative Adversarial Networks For Load Scenario Generation<br><sub>Official GitHub repository for the Elsevier Energy and AI paper</sub>

![Graphical abstract](https://github.com/Advestis/els_paper/blob/master/graphical_abstract.png)

**Stress Testing Electrical Grids: Generative Adversarial Networks For Load Scenario Generation**<br>
Matteo Rizzato, Nicolas Morizet, William Maréchal and Christophe Geissler<br>
DOI: https://doi.org/10.1016/j.egyai.2022.100177<br>

**Abstract**: *As the energy transition is upon us, the replacement of combustion engines by electrical ones will imply a greater stress on the electrical grid of different countries. Therefore, it is of paramount importance to simulate a great number of hypothetical multi-variant scenarios to correctly plan the roll-out of new grids. In this paper, we deploy Generative Adversarial Networks (GANs) to swiftly reproduce the non-Gaussian and multimodal distribution of real energy-related samples, making GANs a valuable tool for data generation in the field. In particular, we propose an original dataset deriving from the aggregation of two European providers including hourly electric inland generation from several European countries. This dataset also comes along with the corresponding season, day of the week, hour of the day and macro-economic variables aiming at unequivocally describing the country's energetic profile. Finally, we evaluate the performance of our model via dedicated metrics capable of grasping the non-Gaussian nature of the data and compare it with the state-of-the-art model for tabular data generation.*

**Dataset**: https://storage.googleapis.com/neg_dataset_eu/data_set.csv

**Proposed Model**: https://storage.googleapis.com/els-models/proposed_GAN_model.zip

## Working example

**Requirements**
- Tensorflow 2.9.1
- Numpy 1.23.2
- Pandas 1.4.3
- Getdist 1.3.4

**Data generation**

The pre-trained generator is publicly available for you to obtain a batch of synthetic data. In order to use it, please run the following commands within a `Python` shell or script 
````
    # loading pre-trained model
    generator = tf.keras.models.load_model("~/path/to/proposed_GAN_model/generator")

    # generate a batch of synthetic data
    n_points = int(1e5)
    latent_dim = 40
    with tf.device('/cpu:0'):
        noise = tf.random.normal(shape=(n_points, latent_dim))
        gen_data = generator(noise).numpy()
````
The desired data will be available as Numpy array in the `gen_data` variabale.

The generated data can be further deployed in the desired applications. For example, we can reproduce Fig.8 comparing them to the real dataset via the following script

```
    # loading real dataset
    real_data = pd.read_csv("~/path/to/proposed_GAN_model/data_set.csv", index_col=0).values
    
    # lookig at similarity via triagular plot
    variables_names = ['elec.load', 'elec.prices', 'gas prices', 'GDP-growth', 'population',
                       'degree-day', 'season', 'day in week', 'night/day']
                       
    samples = MCSamples(samples=real_data[:, :6], names=variables_names[:6],
                        settings={'boundary_correction_order': 0,
                                  'mult_bias_correction_order': 0,
                                  'smooth_scale_2D': 0.1,
                                  'smooth_scale_1D': 0.1}
                        )

    samples2 = MCSamples(samples=gen_data[:, :6], names=variables_names[:6],
                         settings={'boundary_correction_order': 0,
                                   'mult_bias_correction_order': 0,
                                   'smooth_scale_2D': 0.05,
                                   'smooth_scale_1D': 0.1})
    g = plots.get_subplot_plotter()
    
    g.triangle_plot([samples, samples2],
                    legend_labels=['real data', 'generated data'],
                    shaded=True,
                    contour_colors=['blue', 'red'],
                    contour_lws=[0.5, 1])

    g.fig.savefig('fig8.pdf')
```


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
