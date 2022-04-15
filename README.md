https://blog.csdn.net/ydm19891101/article/details/104505624/
CUDA_VISIBLE_DEVICES=0,1 nohup python -m torch.distributed.launch --nproc_per_node=2 --master_port=$RANDOM train.py \
--pretrain=False \
--skipattn=True \
--cat=True \
--img_attn_layers=4 \
--query_attn_layers=2 \
--num_query=16 \
--sgd=True \
--train_list='list/MOTS/MOTS_train_01.txt' \
--snapshot_dir='snapshots/CQTr_adamlr1e2_1500_liki_add16q' \
--input_size='64,192,192' \
--batch_size=4 \
--num_gpus=2 \
--num_epochs=1500 \
--num_cls=2 \
--output_channel=2 \
--start_epoch=0 \
--learning_rate=0.01 \
--num_workers=4 \
--random_scale=True \
--FP16=False \
--weight_std=False \
--random_mirror=True \
--itrs_each_epoch=40 \
>> train_result_adam16q_liki.txt &
