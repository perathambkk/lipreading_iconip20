# Lipreading

A reporitory for lipreading on the [lipreading in the wild (LRW) dataset](https://www.robots.ox.ac.uk/~vgg/data/lip_reading/lrw1.html) using the SpotFast Networks (ICONIP 2020). 
The SpotFast Networks utilize temporal window, two input pathways with lateral connections and two memory-augmented transformers to recognize word-level lip movements. The test accuracy is 84.4%. For comparisons with other methods, please consider [PapersWithCode](https://paperswithcode.com/sota/lipreading-on-lip-reading-in-the-wild). 

The models (most in this task, at the very least) are sensitive to random seeds, as far as I feel. Mixing random seeds between epoch cycles (like every 5 epochs in CosineAnnealing, setting T_max=5) improves the results surprisingly (if epoch % 5 == 0: set_seed(seeds[s_i+1]) s_i += 1 etc. I used my apartment numbers as seeds.). It is normal if training on different machines gives slightly different results. My published results are from the UMD CVL server nodes which yield different numbers compared to training on my local machine also. Even slightest in hyperparameters or settings, such as the number of multi-gpu nodes or the number of cpu dataloader workers, gives slightly different results. My published results are exactly reproducible on, at least, UMD CVL server nodes or any machines with similar configurations using the provided SLURM scripts. This also happens in some preceeding works, such as [https://github.com/mpc001/end-to-end-lipreading](https://github.com/mpc001/end-to-end-lipreading) and in its issue section [https://github.com/mpc001/end-to-end-lipreading/issues/6](https://github.com/mpc001/end-to-end-lipreading/issues/6) where the authors used the SEED 1 in the Imperial College London university server setting. There are other papers in lipreading mentioning this. Also, there are also other papers where the training data order matters a lot. Everyone reports the results from the best seed they found as it seems.... apart from their other contributions.

Since this task datasets are mostly large scale and there is an affiliation wall on this task, I personally do not see anyone doing any insightful example/model mining on this issue. It takes lots of computational power also even if we may filter or minimize the dataset (500k short clips LRW take days to train, even on small models using a P5000). Most submissions in the PapersWithCode are currently (@2024) around almost 90% for single model performances without explicit word boundaries.

Wiriyathammabhum, Peratham. "SpotFast Networks with Memory Augmented Lateral Transformers for Lipreading." 
International Conference on Neural Information Processing. Springer, Cham, 2020.

## Training and Testing
run main*.py, such as [short1.27fast_nlls_xl_2mem_lattransconv_p_OSL_500_cosine/maint3.py](short1.27fast_nlls_xl_2mem_lattransconv_p_OSL_500_cosine/maint3.py), after specifying the lrcodebase folder and other dependencies. For the [LRW dataset](https://www.robots.ox.ac.uk/~vgg/data/lip_reading/lrw1.html), please download the data and fill in the BBC agreement at the [BBC Lip Reading in the Wild and Lip Reading Sentences in the Wild Datasets page](https://www.bbc.co.uk/rd/projects/lip-reading-datasets). A valid institutional affiliation is needed. 

*The model file is also copyrighted by the agreement since it is a derivative from the LRW dataset, unless otherwise stated. So, the checkpoint is not provided here.*

## Citation
A link to the [paper](https://link.springer.com/chapter/10.1007/978-3-030-63820-7_63) and its [ArXiv](https://arxiv.org/abs/2005.10903).

### Cite this paper

Wiriyathammabhum, P. (2020). SpotFast Networks with Memory Augmented Lateral Transformers for Lipreading. In: Yang, H., Pasupa, K., Leung, A.CS., Kwok, J.T., Chan, J.H., King, I. (eds) Neural Information Processing. ICONIP 2020. Communications in Computer and Information Science, vol 1332. Springer, Cham. https://doi.org/10.1007/978-3-030-63820-7_63

```bixtex
@inproceedings{wiriyathammabhum2020spotfast,
  title={SpotFast Networks with Memory Augmented Lateral Transformers for Lipreading},
  author={Wiriyathammabhum, Peratham},
  booktitle={International Conference on Neural Information Processing},
  pages={554--561},
  year={2020},
  organization={Springer}
}
```
]
