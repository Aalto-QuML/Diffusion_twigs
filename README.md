# Diffusion Twigs with Loop Guidance for Conditional Graph Generation

 [Giangiacomo Mercatali*](https://www.semanticscholar.org/author/Giangiacomo-Mercatali/2126963336) |  [Yogesh verma*](https://yoverma.github.io/yoerma.github.io/) | [Andre Freitas](https://andrefreitas.org/) |  [Vikas Garg](https://www.mit.edu/~vgarg/)
 
This repository includes the supporting code for:

Giangiacomo Mercatali*, Yogesh Verma*, Andre Freitas, Vikas Garg. **Diffusion Twigs with Loop Guidance for Conditional Graph Generation**. In Advances in Neural Information Processing Systems 38, 2024.

<p align="center">
  <img src="https://github.com/Aalto-QuML/Diffusion_twigs/blob/main/model_flow.png" />
</p>


# Twigs



## Environment installation
Install packages in `env.yml`. Tested on pytorch `1.13.1        py3.8_0`


## QM9 Dataset
Download preprocessed data (by Huang et al 2023) found at [this link](https://zenodo.org/record/7966493) into the `data` folder.

## Model Arguments
Use the option `--config.model.name=cond_DGT_concat` to run `Jodo` from Huang et al. 2023.


## Train Twigs: 2 properties
Pairs: `(Cv,Mu), (Gap,Mu), (alpha,Mu)`.
```bash
CUDA_VISIBLE_DEVICES=0 python main.py --config configs/vpsde_qm9_cond_multi_twigs.py --config.model.name=cond_DGT_twigs --config.training.n_iters=3000000 --mode train --config.nprops=2 --config.model.cond_ch=2 --workdir exp_cond_multi/vpsde_qm9_cond_twigs_Cv_mu --config.cond_property1 Cv --config.cond_property2 mu
CUDA_VISIBLE_DEVICES=0 python main.py --config configs/vpsde_qm9_cond_multi_twigs.py --config.model.name=cond_DGT_twigs --config.training.n_iters=3000000 --mode train --config.nprops=2 --config.model.cond_ch=2 --workdir exp_cond_multi/vpsde_qm9_cond_twigs_gap_mu --config.cond_property1 gap --config.cond_property2 mu --config.training.snapshot_freq=100000
CUDA_VISIBLE_DEVICES=0 python main.py --config configs/vpsde_qm9_cond_multi_twigs.py --config.model.name=cond_DGT_twigs --config.training.n_iters=3000000 --mode train --config.nprops=2 --config.model.cond_ch=2 --workdir exp_cond_multi/vpsde_qm9_cond_twigs_alpha_mu --config.cond_property1 alpha --config.cond_property2 mu --config.training.snapshot_freq=100000
```

## Sample Twigs: 2 properties
```bash
ckpt=100
CUDA_VISIBLE_DEVICES=0 python main.py --config configs/vpsde_qm9_cond_multi_twigs.py --config.model.name=cond_DGT_twigs --mode eval --config.nprops=2 --config.model.cond_ch=2 --workdir exp_cond_multi/vpsde_qm9_cond_twigs_Cv_mu --config.cond_property1 Cv --config.cond_property2 mu --config.eval.save_graph=True --config.eval.ckpts=$ckpt
CUDA_VISIBLE_DEVICES=0 python main.py --config configs/vpsde_qm9_cond_multi_twigs.py --config.model.name=cond_DGT_twigs --mode eval --config.nprops=2 --config.model.cond_ch=2 --workdir exp_cond_multi/vpsde_qm9_cond_twigs_gap_mu --config.cond_property1 gap --config.cond_property2 mu --config.eval.save_graph=True --config.eval.ckpts=$ckpt
CUDA_VISIBLE_DEVICES=0 python main.py --config configs/vpsde_qm9_cond_multi_twigs.py --config.model.name=cond_DGT_twigs --mode eval --config.nprops=2 --config.model.cond_ch=2 --workdir exp_cond_multi/vpsde_qm9_cond_twigs_alpha_mu --config.cond_property1 alpha --config.cond_property2 mu --config.eval.save_graph=True --config.eval.ckpts=$ckpt
```

## Train Twigs: 3 properties
properties: `alpha,mu,gap`
```bash
CUDA_VISIBLE_DEVICES=0 python main.py --config configs/vpsde_qm9_cond_multi_twigs.py --config.model.name=cond_DGT_twigs --config.training.n_iters=3000000 --mode train --config.nprops=3 --config.model.cond_ch=3 --workdir exp_cond_multi/vpsde_qm9_cond_twigs_alpha_mu_gap --config.cond_property1 alpha --config.cond_property2 mu --config.cond_property3 gap --config.training.snapshot_freq=100000
```

## Sample Twigs: 3 properties
```bash
CUDA_VISIBLE_DEVICES=0 python main.py --config configs/vpsde_qm9_cond_multi_twigs.py --config.model.name=cond_DGT_twigs --mode eval --config.nprops=3 --config.model.cond_ch=3 --workdir exp_cond_multi/vpsde_qm9_cond_twigs_alpha_mu_gap --config.cond_property1 alpha --config.cond_property2 mu --config.cond_property3 gap --config.eval.save_graph=True --config.eval.ckpts=$ckpt
```




## Citation
If you find this repository useful in your research, please consider citing the following paper:
 ```
@inproceedings{
diffusiontwigs,
title={Diffusion Twigs with Loop Guidance for Conditional Graph Generation},
author= {Mercatali, Giangiacomo and Verma, Yogesh and Freitas, Andre and Garg, Vikas},
booktitle={The Thirty-eighth Annual Conference on Neural Information Processing Systems},
year={2024},
url={https://openreview.net/forum?id=fvOCJAAYLx}
}

```


