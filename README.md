# Cat-Dog-Image-Recognition-CNN
In this project, using ConVnet and DenseNet201, I create a model that can distinguish between photos of cats and dogs with the help of the Keras library.

# Metadata
In this project, the original dataset is a binary MATLAB file about the images of cats and dogs. 
The original data, the dictionary structure, is composed of four pairs of keys and values:

Key: "X"; A set of numerical attributes that represent image data is stored in this key. This data has dimensions of (4096, 242), where a picture is in each column and a vector with information about that image is in each row. 

Key: "G"; This key corresponds to labels that hold a list of binary data. A "dog" is represented by the value "1," and a "cat" by the value "0." The genuine labels for every associated image in the dataset are supplied by this key.

Keys: “px” and "py"; Each image in the dataset's width ('nx') and height ('ny') are represented by integer values that are stored in these keys. Each image's width and height can be understood by referring to these values, which depict the image dimensions.

# Data Preprocessing
During this phase, the manipulation of the feature matrix "X" involves several data preprocessing steps:
Transposition of "X": The original dimensions of "X" are altered to (242, 4096), signifying that each row now encapsulates comprehensive information about individual dogs or cats.
Normalization of "X": Employing minimum and maximum normalization across the entire dataset, all values are transformed into the range [0, 1].
Reshaping of "X": Based on the image dimensions denoted by the variables "px" and "py," the feature matrix assumes a multidimensional shape of (242, 64, 64, 1). This signifies the presence of 242 images in total, each with a pixel size of 64 by 64, and all images are in grayscale.
Conversion to RGB Scale: Given that the input images have a shape of 64x64 and there are 242 samples, each with 4096 features, the utilization of the DenseNet201 model becomes imperative. 
However, this model expects an input shape of (224, 224, 3). To align with this requirement, the code undergoes adjustment, specifically reshaping the matrix "X" into a three-channel format with dimensions (242, 224, 224, 3). This modification is indispensable as the DenseNet-201 model architecture stipulates that input images must conform to a size of 224.
Transpose of Images: The images undergo a 90-degree clockwise rotation by swapping the height and width dimensions.

# Train and Test data Split
In this scenario, the original target data ratio will be preserved when dividing the preprocessed 
data into the training and test sets. Consequently, in both the training and test sets, the number 
of data points whose designated labels are 0 and 1 is almost equal.

# Model Creation (DenseNet201)
In this application, the DenseNet201 model is utilized for the dataset, and all its layers are organized through the Keras framework from the Tensorflow library. The DenseNet-201 model architecture mandates that the input images be of size (224, 224, 3 channels). Frequently employed as a feature extractor in transfer learning, DenseNet201 utilizes ReLU activation 
functions within its hidden layers, including the pre-trained layers of the base model.

