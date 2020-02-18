# distributed_ffn
Distributed training of Flood-Filling Networks (FFNs) for instance segmentation in 3d volumes implemented with Horovod.
For more details, please see our paper ["Scaling Distributed Training of Flood-Filling Networks on HPC Infrastructure for Brain Mapping"](https://ieeexplore.ieee.org/abstract/document/8945106).

Abstract: Mapping all the neurons in the brain requires automatic reconstruction of entire cells from volume electron microscopy data. The flood-filling networks (FFN) architecture can achieve leading performance. However, the training of the network is computationally very expensive. In order to reduce the training time, we implemented synchronous and data-parallel distributed training using the Horovod framework on top of the published FFN code. We demonstrated the scaling of FFN training up to 1024 Intel Knights Landing (KNL) nodes at Argonne Leadership Computing Facility. We investigated the training accuracy with different optimizers, learning rates, and optional warm-up periods. We discovered that square root scaling for learning rate works best beyond 16 nodes, which is contrary to the case of smaller number of nodes, where linear learning rate scaling with warm-up performs the best. Our distributed training reaches 95\% accuracy in approximately 4.5 hours on 1024 KNL nodes using Adam optimizer.

![Learning rate scaling](https://wushidonguc.github.io/assets/lr_acc.png)

![Training curves](https://wushidonguc.github.io/assets/training.png)


## References

*  [[1] Flood-Filling Networks (Google's original asynchronous version)](https://github.com/google/ffn)
*  [[2] Horovod: Distributed training framework for TensorFlow.](https://github.com/uber/horovod)
*  [[3] Scaling Distributed Training of Flood-Filling Networks on HPC Infrastructure for Brain Mapping](https://ieeexplore.ieee.org/abstract/document/8945106)
