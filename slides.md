---
marp: true
# theme: gaia
# theme: uncover
# _class: lead
paginate: true
backgroundColor: #fff
title: Neutronics Workshop
description: Presentation slides for the fusion energy neutronics workshop
author: Jonathan Shimwell
keywords: fusion,neutronics,neutron,photon,radiation,simulation,openmc,dagmc
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem;
  }
---

<style>
  :root {
    --color-background: #fff;
    --color-foreground: #333;
    --color-highlight: #f96;
    --color-dimmed: #888;
  }
  {
    font-size: 29px
  }
  code {
    white-space : pre-wrap !important;
    word-break: break-word;
  }
  .columns
  {
      /* font-family:    Arial, Helvetica, sans-serif; */
      font-size:      20px;
      /* font-weight:    bold; */
  }
  /* h1 {
    font-family: Courier New;
  } */
</style>


# Fusion Neutronics Workshop


![Neutron](images/cover.png)

---


# Why is neutronics useful


![bg vertical height:15cm left:10%](images/why_neutronics.png)
- **Radioactivity** - Neutrons activate material, making it radioactive leading to handling and waste storage requirements.​
- **Hazardous** - Neutrons are Hazardous to health and shielded will be needed to protect the workforce.​
- ***Produce fuel*** - Neutrons will be needed to convert lithium into tritium to fuel the reactor.​
- ***Electricity*** - 80% of the energy release by each DT reaction is transferred to the neutron.​
- ***Structural integrity*** - Neutrons cause damage to materials such as embrittlement, swelling, change conductivity …​
- ***Diagnose*** - Neutrons are an important method of measuring a variety of plasma parameters (e.g. Q value).​

---

# Topics Covered Half Day Course

- Neutron and Photon interaction cross sections

- Material creation

- Particle sources

- Constructive Solid Geometry (CSG)

- Tallies (heat, tritium breeding ratio, damage, flux)

- Neutron activation

---

# Getting started

- 🐋 Install Docker

- 🔽 Download the docker image

- 🏃Run the docker image

- 🔗 Navigate to the URL in the terminal

Detailed instructions are on [GitHub](https://github.com/fusion-energy/neutronics-workshop/tree/main#local-installation)

---

# Containers

![bg right:40% 100%](https://imgs.xkcd.com/comics/python_environment.png)

Install single package (Docker) and avoid installing a few hundred packages.

- Portable
- Reproducible
- Security
- Isolation
- Deployable

---

# Tasks

![bg right:50% 100%](images/jupyter.png)
- Collection of Jupyter notebooks

- Separate task folder for each topic

- Learning outcomes for each task

- Simulation outputs include:
    - numbers
    - graphs
    - images
    - 3D visualization.

---

# OpenMC

<!-- [![bg right:60% 80%](https://api.star-history.com/svg?repos=openmc-dev/openmc&type=Date)](https://star-history.com/#openmc-dev/openmc&Date) -->
[![bg right:60% 80%](images/stars.png)](https://star-history.com/#openmc-dev/openmc&Date)

- Increasing adoption
- Supportive community
- GitHub repository
- Permissive license
- Python API

---

![bg right:45% 100%](images/get_started.png)

# Getting started

1. Run the docker image
    ```docker run -p 8888:8888 ghcr.io/fusion-energy/neutronics-workshop```

2. Double click on the ```half-day-workshop``` folder circled in red.



---


# Timetable

<div class="columns">
<div>

- 9.00 Introduction presentation  10
- 9.10 Plotting cross sections    30
    - task_01_isotope_xs_plot
    - task_02_element_xs_plot
    - task_03_material_xs_plot
- 9.40 Making materials            15
    - task_04_example_materials_from_isotopes
    - task_05_example_materials_from_elements
- 9.55 Geometry                   20
    - task_06_simple_csg_geometry
- 10.15 Break                      15
- 10.30 Plotting particles        35
  - task_07_point_source_plots
  - task_08_ring_source
  - task_09_plasma_source_plots

</div>
<div>

- 11.05 Tritium Breeding Ratio (TBR)    10
  - task_10_example_tritium_production
- 11.15 Damage (DPA)                    15
  - task_11_find_dpa
- 11:30 Break                           15
- 11:45 neutron photon spectra          30
  - task_12_example_neutron_spectra_on_cell  
  - task_13_example_photon_spectra
- 12.15 mesh tallies                    15
  - task_14_example_2d_regular_mesh_tallies
- 12.30 mesh tallies                    15
  - task_15_full_pulse_schedule
- 12.45 Putting it all together         15
  - task_16_optimal_design

</div>
</div>

---
# Task 1, 2, 3
# Microscopic Cross Sections

- Probability of interaction is characterised by the microscopic cross-section (σ). It is the effective size of the nucleus.

- Cross section data is key to the neutronics workflow and provide us with the likelihood of a particular interaction.

- Cross sections can be measured experimentally with monoenergetic neutrons.

---
# Experimental data

Availability of experimental data varies for different reactions and different isotopes.

Typically the experimental data is then interpreted to create evaluation libraries, such as ENDF, JEFF, JENDL, CENDL.

[![bg right:45% 100%](images/exfor_be_n_2n.png)](https://nds.iaea.org/dataexplorer/)


---
# Cross section reactions

Cross section evaluations exist for:

- different nuclides
- different interactions.

A list of reactions available in OpenMC is [here](https://docs.openmc.org/en/stable/usersguide/tallies.html#id2)

For example Be9(n,2n)2He would be a neutron interaction with beryllium 9 which results in 2 neutrons and 2 helium nuclei.

---

# Reaction rate

The reaction rate ($RR$) can be found by knowing the number of neutrons per unit volume ($n$), the velocity of neutrons ($v$), the material density ($p$), Avogadro's number ($N_{a}$), the microscopic cross section at the neutron energy ($\sigma_{e}$) and the atomic weight of the material ($M$). This reduces down to the neutron flux ($\phi$), nuclide number density ($N_{d}$) and microscopic cross section\sigma_{e}. This can be reduced one more stage by making use of the Macroscopic cross section ($\Sigma_{e}$).


$$ RR = \frac{nv\rho N_{a}\sigma_{e} }{M} = \phi N_{d} \sigma_{e} = \phi \Sigma_{e} $$
