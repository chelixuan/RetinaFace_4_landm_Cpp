# RetinaFace C++

This is the C++ implementation of the [Retinaface PyTorch](https://github.com/biubug6/Pytorch_Retinaface) model inference.

# 1. Modified 
### original
The Inference Engine used is the [ONNX Runtime](https://onnxruntime.ai/) Framework, and the model is obtained through the PyTorch ONNX export API. A pretrained model is provided in [this path](model/retinaface_dynamic.zip) with dynamic input shape. 

In the [luisfmnunes/RetinaFacesCpp](https://github.com/luisfmnunes/RetinaFacesCpp) implementation, images with any dimension above 640px are resized to 640x640 letterbox padding, due to anchors decoding limitation.

### clx modified
In the current implementation, images with any dimension will be resized to 1280*720(or 640*480 with mini input shape onnx model). The pretrained onnx model is provided in [this path](model/raw_mobilenet0.25_Final_sim.onnx)  with fixed input shape.

# 2. Usage

Bellow are the usage instructions

### Compiling the main example

If a custom trained model is intended to be used, modify the [main script](main.cpp) in order to provide the correct path for model loading.

Use the following instructions to compile the [main script](main.cpp):

```
mkdir build && cd build
cmake ..

make
```
<image align="center" src="make_process.png">

# 3. Testing on an image

If the compilation succeded a binary file called RetinaCpp will be generated into the build directory, which can be used to detect faces in an image using the following structure:

```
./RetinaCpp PATH_TO_IMAGE
```

where **PATH_TO_IMAGE** should be replaced with a path to an image file.

