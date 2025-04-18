# GradientVis

**GradientVis** is a Python library designed for visualizing neural network gradients, aimed at helping researchers and developers better interpret the inner workings of deep learning models. It includes various gradient visualization methods such as **GradCAM**, **SmoothGrad**, and **Integrated Gradients** to make model interpretation easier.

## Functions

- **GradCAM**: Visualize the regions of an image that a CNN model is focusing on for a given class.
- **SmoothGrad**: Reduce noise in gradient-based visualizations by adding noise to the input and averaging.
- **Integrated Gradients**: A method for attributing the prediction of a neural network to its input features.
- **Postprocessing**: Normalize and prepare visualizations for easier interpretation and presentation.

## Installation

You can install `gradientvis` via **pip** directly from the repository:

```bash
pip install gradientvis
```

## Usage

### 1. **GradCAM Example**

```python
from gradientvis.methods.gradcam import GradCAM
from gradientvis.utils.preprocessing import preprocess_image

# Load your model (e.g., a CNN)
model = ...

# Preprocess your input image
image = preprocess_image("path_to_your_image.jpg")

# Generate GradCAM visualization
gradcam = GradCAM(model, model.layer4)  # Specify the target layer
cam = gradcam.generate(image, class_idx=0)

# Display the results
import matplotlib.pyplot as plt
plt.imshow(cam, cmap='jet')
plt.show()
```

### 2. **SmoothGrad Example**

```python
from gradientvis.methods.smoothgrad import SmoothGrad
from gradientvis.utils.preprocessing import preprocess_image

# Load your model and image
model = ...
image = preprocess_image("path_to_your_image.jpg")

# Generate SmoothGrad visualization
smoothgrad = SmoothGrad(model)
grad = smoothgrad.generate(image, class_idx=0)

# Display the results
import matplotlib.pyplot as plt
plt.imshow(grad, cmap='jet')
plt.show()
```

### 3. **Integrated Gradients Example**

```python
from gradientvis.methods.integrated_gradients import IntegratedGradients
from gradientvis.utils.preprocessing import preprocess_image

# Load your model and image
model = ...
image = preprocess_image("path_to_your_image.jpg")

# Generate Integrated Gradients visualization
integrated_gradients = IntegratedGradients(model)
integrated_grad = integrated_gradients.generate(image, class_idx=0)

# Display the results
import matplotlib.pyplot as plt
plt.imshow(integrated_grad, cmap='jet')
plt.show()
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
