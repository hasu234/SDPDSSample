## Dependencies

* Python 3.9

## Setting up  conda Environment

* Clone the repository by running 
```
git clone https://github.com/hasu234/SDPDSSample.git
```
* Change current directory to SDPDSSample 
```
cd SDPDSSample
```
* Create a conda environmet 
```
conda create -n myenv python=3.9
```
* Activate the environment 
```
conda activate myenv
```
* Install the required library from ```requirment.txt``` by running 
```
pip install -r requirmen.txt
```
* Or, create a conda environment from ```environment.yml``` by running 
```
conda env create -f environment.yml
```

## Trining your data
* To train your own dataset
Make sure you have a data folder having the same folder hiararchy like below
```
├── dataset
|   ├── train
│   │   ├── class1
│   │   │   ├──image1.jpg
│   │   │   ├──image2.jpg
│   │   ├── class2
│   │   │   ├──image1.jpg
│   │   │   ├──image2.jpg
│   │   ├── class3
│   │   │   ├──image1.jpg
│   │   │   ├──image2.jpg
│   │   ├── class4
│   │   │   ├──image1.jpg
│   │   │   ├──image2.jpg
|   ├── test
│   │   ├── class1
│   │   │   ├──image1.jpg
│   │   │   ├──image2.jpg
│   │   ├── class2
│   │   │   ├──image1.jpg
│   │   │   ├──image2.jpg
│   │   ├── class3
│   │   │   ├──image1.jpg
│   │   │   ├──image2.jpg
│   │   ├── class4
│   │   │   ├──image1.jpg
│   │   │   ├──image2.jpg
```
or make some chainges on ```train.py``` according to to your dataset directory.
* Make sure you are in the project directory and run the ```train.py``` script with the folder directory of your dataset
```
python train.py /path/to/dataset_directory
```
## Running inference
* To run the inference on your test data make sure you downloaded the pretrained model from [this link](https://drive.google.com/uc?id=197Kuuo4LhHunYLgGKfGeouNTL0WguP0T&export=download).
* Then run the ```infer.py``` script from terminal specifying the test image location and downloaded pretrained model location
```
python infer.py path/to/image.jpg path/to/model.pth
```


## Running on Docker
* Clone the repository by running 
```
git clone https://github.com/hasu234/SDPDSSample.git
```
* Change current directory to SDPDSSample 
```
cd SDPDSSample
```
* Build the Docker image by running 
```
docker build -t sdpdsample .
```
* Run the docker image 
```
docker run -d sdpdsample
```
if the container failed to run in background, run it on foreground using ```docker run -it sdpdsample``` then exit to get the running container id
* Get the container id
```
docker ps
```
* Getting inside the container
```
docker exec -it <container id> bash
```
You will get a Linux like command-line interface
* Running the project
```
# for training your data
python train.py /path/to/dataset_directory

# for running inference
python infer.py path/to/image.jpg path/to/model.pth
```
