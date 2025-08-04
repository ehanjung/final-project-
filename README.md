# final-project-

whew i got the dataset https://www.kaggle.com/datasets/kritikseth/fruit-and-vegetable-image-recognition?select=test

what codes i used to train the model
(jetson inference on nvidia jetson orin nano)
cd ~/jetson-inference/
./docker/run.sh

cd python/training/classification

python3 train.py --model-dir=models/testdataset data/testdataset

python3 onnx_export.py --model-dir=models/testdataset

NET=models/testdataset
DATASET=data/testdataset

imagenet.py \
  --model=$NET/resnet18.onnx \
  --labels=$NET/labels.txt \
  --input_blob=input_0 \
  --output_blob=output_0 \
  $DATASET/test/apple/image_1.jpg output.jpg
