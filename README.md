# Approach2-Style-Transfer-Using-Motion-Manifold

In this project, we are aiming for  identifing which aspects of the character animation affect the user’s perception and interaction with the character (agent). Therefore we applied a framework taken from Daniel Holden work that synthesize character movements based on high level parameters, such that the produced movements respect the manifold of human motion, trained on a large motion capture dataset. This system use a Gram Matrix to apply a specific style to a a specific content. 

## Attribution

The core code used in this project was created by Daniel Holden et al. [Link-to-original-code](https://theorangeduck.com/page/publications). Their paper can be found 
[Here](https://theorangeduck.com/media/uploads/motionsynthesis.pdf).

## Modifications and Use Case

I have adapted the original code to suit the requirements of my use case. The modifications include retraining the model with our proper dataset. 

## How to Use

This is the code and data for the paper of the above title. It consists of a 
large motion database containing several external databases retargetted to 
a single skeleton structure, as well as the code for the paper implemented in 
Theano.

Here is an overview of the structure:

    `data`    - The motion database and data processing scripts
    `motion`  - A helper library for dealing with motion data
    `nn`      - A custom Theano library for neural networks
    `synth`   - Code, examples, and demos used in the paper
    
Quickstart
----------

Once you have installed Theano, Numpy, Scipy, as the network is already trained 
and the data already preprocessed, you can start by running any of the demo 
scripts in the `synth` directory.



Processing
----------


### Stage 1

The databases are processed in two stages. First the databases in the 
`external` folder are retargetted to a unified skeleton structure defined by 
the first capture in the CMU database. This is performed using all of the 
scripts inside the `processed` folder starting with the word `retarget`.

This stage places a number of subfolders in the `processed` directory 
containing all the .bvh files for all of the databases. These retargetting 
scripts have already been run so you will see these folder already exist. The
scripts only need to be re-run if some issues are found in the retargetting and
it needs to be adjusted.


### Stage 2

The second stage is performed by the `export.py` script in the `processed` 
folder. This script converts the data into the format used by the paper and 
does many processes such as placing the motion on the floor, making the pose 
local to the forward direction and annotating the foot contacts.

This stage puts a number of `.npz` files inside the `processed` folder. As 
before, these are included and as such this script only needs to be re-run if 
there is some adjustment to the required processing.

Once processed the script `view.py` in the `processed` folder can be used to 
view data in this format back using `matplotlib`.

Go to motionsynth_code -> synth
for training:
```python
python train.py
```
for testing:
```python
python demo_style_transfer.py
```





I would like to express my gratitude to Holden et al. for creating the initial codebase. Their contribution laid the groundwork for the enhancements made in this project.

## Contact

If you have any questions, suggestions, or feedback, feel free to reach out to me at ghammaz.ali1@gmail.com .
