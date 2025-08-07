# <p align="center">Contrast-Invariant Self-supervised Segmentation for Quantitative Placental MRI</p>

This is the official implementation of the paper  
**"Contrast-Invariant Self-supervised Segmentation for Quantitative Placental MRI"**  
presented at the [**MICCAI PIPPI Workshop 2025**](https://arxiv.org/abs/2505.24739).

---

## <p align="center"> Schematic Overview</p>

<p float="left">
  <img src="https://github.com/ygritte723/coninv-MRI/blob/master/images/semantic_mae_architecture.png" width="40%" />
  <img src="https://github.com/ygritte723/coninv-MRI/blob/master/images/semantic_mpl_architecture.png" width="50%" />
</p>

- **(a) MAE Pretraining:** Multi-echo slices are masked and encoded using a shared encoder. The training objective includes a reconstruction loss ($\mathcal{L}_{\text{MSE}}$), semantic consistency ($\mathcal{L}_{\text{SC}}$), and global-local collaboration alignment ($\mathcal{L}_{\text{Cos}}$).

- **(b) MPL Training:** A teacher-student framework is used to leverage pseudo-labels on unlabeled target slices. The teacher model $F_\theta$ is updated via exponential moving average (EMA), while the student model $F_\phi$ is optimized using the MPL loss ($\mathcal{L}_{\text{MPL}}$).
---

## <p align="center"> Segmentation Results Across Echo Times</p>

![](https://github.com/ygritte723/coninv-MRI/blob/master/images/comparison_1.png)

**Qualitative comparison of segmentation across echo times (TE1–TE8).**  
Each row shows the input slice, model predictions (red overlay), and the ground truth.  Our method achieves consistent and accurate boundaries under varying contrast conditions.

---


# <p> Steps to reproduce</p>


## <p>  Preliminaries  </p> 

This project was developed and tested with:

- Python 3.8.5  
- PyTorch 1.11.0  
- GPU: NVIDIA H100 (40G)  
- Conda environment defined in `requirements.txt`

To set up the environment:

```bash
cd archive/plac_seg_proj/code
conda create -n plac_seg python=3.8
conda activate plac_seg
pip install -r requirements.txt
```


For training: 
    
    ```
    python train.py --config=YOUR_PATH_TO_YAML
    ```
Training procedure:
    

For inference: 

   ``` python test.py # be sure to edit the test.py
```

Parameters and data structure: 
There is a **detailed** explanation in [/cfg/default.py](https://github.com/ygritte723/coninv-MRI/blob/master/cfg/default.py).


## <p> Cite </p>
Please cite our paper if you use this code in your own work:<br>

@article{zhong2025contrast,
  title={Contrast-Invariant Self-supervised Segmentation for Quantitative Placental MRI},
  author={Zhong, Xinliu and Liu, Ruiying and Nichols, Emily S and Zhang, Xuzhe and Laine, Andrew F and Duerden, Emma G and Wang, Yun},
  journal={arXiv preprint arXiv:2505.24739},
  year={2025}
}




