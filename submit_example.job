#!/bin/bash
#COBALT -t 59
#COBALT -n 64
#COBALT --attrs mcdram=cache:numa=quad
#COBALT -A datascience
#COBALT -q debug-cache-quad
#COBALT -M dongws@uchicago.edu
module add miniconda-3.6/conda-4.4.10
source activate /lus/theta-fs0/projects/datascience/keceli/miniconda3

# Number of MPI ranks per node
PPN=1
export OMP_NUM_THREADS=128

train_dir=${PWD}/models/test

aprun -n $((${COBALT_PARTSIZE} * ${PPN})) -N ${PPN} -d 128 -j 2 -cc depth -b /lus/theta-fs0/projects/datascience/keceli/miniconda3/bin/python horovod_train.py \
  --train_coords /home/dongws/ffn/ffn/third_party/neuroproof_examples/validation_sample/fib_flyem_validation1_label_lom24_24_24_part14_wbbox_coords-*-of-00025.gz \
  --data_volumes validation1:/home/dongws/ffn/ffn/third_party/neuroproof_examples/validation_sample/grayscale_maps.h5:raw \
  --label_volumes validation1:/home/dongws/ffn/ffn/third_party/neuroproof_examples/validation_sample/groundtruth.h5:stack \
  --model_name convstack_3d.ConvStack3DFFNModel \
  --model_args "{\"depth\": 12, \"fov_size\": [33, 33, 33], \"deltas\": [8, 8, 8]}" \
  --image_mean 128 \
  --image_stddev 33 \
  --max_steps 10000 \
  --summary_rate_secs 60 \
  --train_dir ${train_dir} \
  --batch_size 4 \
  --learning_rate 1e-3 \
  --warmup_steps 2000 \
  --lr_scaling 'linear'



