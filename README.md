# nano-JEPA

nano-JEPA: a Video Joint Embedding Predictive Architecture that runs in a regular computer. Based on [V-JEPA](https://github.com/facebookresearch/jepa).

## Setup

```bash
(base) conda create -n nano-jepa python=3.9 
(base) conda activate nano-jepa

# Install PyTorch on hardware that contains GPUs
# (nano-jepa) conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia

# Install PyTorch only using CPUs 
(nano-jepa) conda install pytorch torchvision torchaudio cpuonly -c pytorch

(nano-jepa) python setup.py install
```

## System directories

Consider using the [nano-datasets](https://github.com/BHI-Research/nano-datasets) tool to create your local configuration. Here is how your local filesystem
should be organized:

```bash
(base) $ tree -d
.
├── image_datasets
│         ├── imagenet_full_size
│         ├── imagenet-mini
└── video_datasets
    └── k400
        ├── train
        └── val
```

At least, two paths must be provided.

### Dataset location path, k400 dataset example

* A Windows user path: C:\Users\your-user\Documents\ML-datasets\video_datasets\k400\k400_file_index.csv
* A Linux user path: /home/your-user/Documents/ML-datasets/video_datasets/k400/k400_file_index.csv

### Logging location path

* A Windows user path: C:\Users\your-user\Documents\ML-logging
* A Linux user path: /home/your-user/Documents/ML-logging

## Run

A set of config files are provided in this repo. Change the paths ins the *.yaml file using the above guidelines.

```bash
# unsupervised training
(nano-jepa)$ python -m app.train_nano_jepa --fname configs/pretrain/vitt.yaml

# video evaluation
(nano-jepa)$ python -m evals.eval_video_nano_jepa  --fname configs/evals/vitt16_k400_16x8x3.yaml

# image evaluation
(nano-jepa)$ python -m evals.eval_image_nano_jepa  --fname configs/evals/vitt16_in1k.yaml

# video inference
(nano-jepa)$ python -m evals.infer_video_classification --fname configs/infer/infer_vitt_k400x8x3.yaml

# visualize feature (work in progress)
(nano-jepa)$ python -m evals.eval_features 
```

## Authors

Paper:

* Title: "nano-JEPA: Democratizing Video Understanding with Personal Computers"
* Authors: Adrián Rostagno, Javier Iparraguirre, Joel Ermantraut, Lucas Tobio, Segundo Foissac, Santiago Aggio, Guillermo Friedrich
* Event: XXV WASI – Workshop Agentes y Sistemas Inteligentes, CACIC.
* Year: 2024.

Bibtex:

```
@inproceedings{ermantraut2020resolucion,
     title={nano-JEPA: Democratizing Video Understanding with Personal Computer},
     author={Adrian Rostagno and Javier Iparraguirre and Joel Ermantraut and Lucas Tobio and Segundo Foissac and Santiago Aggio and Guillermo Friedrich},
     booktitle={XXV WASI – Workshop Agentes y Sistemas Inteligentes, CACIC},
     year={2024}
}
```

### Checkpopints

Here is a list of checkpoints available for experimentation:

<table><thead>
  <tr>
    <th>Model</th>
    <th>Classes</th>
    <th>Train Videos</th>
    <th>Val videos</th>
    <th>Ratio</th>
    <th>Accuracy</th>
    <th>Epochs</th>
    <th>Pre-train</th>
  </tr></thead>
<tbody>
  <tr>
    <td>A (<a href="https://drive.google.com/file/d/15447D6EZkSty0DN-NKR8xJofddPdxLk9/view?usp=sharing" target="_blank" rel="noopener noreferrer">download</a>)</td>
    <td>4</td>
    <td>100</td>
    <td>50</td>
    <td>0.5</td>
    <td>45.50</td>
    <td>20</td>
    <td rowspan="3"><a href="https://drive.google.com/file/d/146WMCv_2S62MgB7MUNaeVuX4YOzmhAXF/view?usp=sharing" target="_blank" rel="noopener noreferrer">nano-JEPA ViT-T 800 videos(download)</a></td>
  </tr>
  <tr>
    <td>B (<a href="https://drive.google.com/file/d/14ySiG4ygDifN04PHGDjBJFTqVaLMCW6o/view?usp=sharing" target="_blank" rel="noopener noreferrer">download</a>)</td>
    <td>4</td>
    <td>25</td>
    <td>12</td>
    <td>0.48</td>
    <td>35.41</td>
    <td>10</td>
  </tr>
  <tr>
    <td>C (<a href="https://drive.google.com/file/d/14wnOom9gzR9ATNXEBfLPyAyHsICqE4ep/view?usp=sharing" target="_blank" rel="noopener noreferrer">download</a>)</td>
    <td>8</td>
    <td>100</td>
    <td>50</td>
    <td>0.5</td>
    <td>41.50</td>
    <td>20</td>
  </tr>
  <tr>
    <td>D (<a href="https://drive.google.com/file/d/155lxtyI4HI-c3KaxJy-FCnq8CgkHmGCJ/view?usp=sharing" target="_blank" rel="noopener noreferrer">download</a>)</td>
    <td>4</td>
    <td>100</td>
    <td>50</td>
    <td>0.5</td>
    <td>99.50</td>
    <td>6</td>
    <td rowspan="3">V-JEPA ViT-L (<a href="https://github.com/facebookresearch/jepa" target="_blank" rel="noopener noreferrer">see V-JEPA site</a>)</td>
  </tr>
  <tr>
    <td>E (<a href="https://drive.google.com/file/d/15GoHxhB7NawX55E1hTaPJSCsj00GyPIC/view?usp=sharing" target="_blank" rel="noopener noreferrer">download</a>)</td>
    <td>4</td>
    <td>25</td>
    <td>12</td>
    <td>0.48</td>
    <td>91.66</td>
    <td>6</td>
  </tr>
  <tr>
    <td>F (<a href="https://drive.google.com/file/d/15IAmP901nkItvi2QcEqyi7ATSPdxwBcI/view?usp=sharing" target="_blank" rel="noopener noreferrer">download</a>)</td>
    <td>8</td>
    <td>100</td>
    <td>50</td>
    <td>0.5</td>
    <td>94.25</td>
    <td>6</td>
  </tr>
</tbody></table>