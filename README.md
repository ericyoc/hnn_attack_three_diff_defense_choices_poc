# Hybrid Neural Network with Three Adversarial Defense Choices

This repository contains an implementation of a Hybrid Neural Network (HNN) that combines a Convolutional Neural Network (CNN) with a Quantum Neural Network (QNN) to classify handwritten digits from the MNIST dataset. The HNN is protected against adversarial attacks using various defense techniques, including input transformation, adversarial training, and randomization.

## Motivating Articles
J. C. Costa, T. Roxo, H. Proença and P. R. M. Inácio, "How Deep Learning Sees the World: A Survey on Adversarial Attacks & Defenses," in IEEE Access, vol. 12, pp. 61113-61136, 2024, doi: 10.1109/ACCESS.2024.3395118. https://ieeexplore.ieee.org/abstract/document/10510296

F. Nesti, A. Biondi and G. Buttazzo, "Detecting Adversarial Examples by Input Transformations, Defense Perturbations, and Voting," in IEEE Transactions on Neural Networks and Learning Systems, vol. 34, no. 3, pp. 1329-1341, March 2023, doi: 10.1109/TNNLS.2021.3105238. https://ieeexplore.ieee.org/abstract/document/9525033

## Results for HNN Model with MNIST Dataset 

### Input Transformation Defense (Results Pending)
Input transformation is a defense technique that aims to preprocess the input data before feeding it into the model. The goal is to make the input more robust and less susceptible to adversarial perturbations. This project implements three input transformation approaches:

1. **Image Quilting:** This technique involves dividing the input image into smaller patches and randomly replacing some of the patches with patches from clean images. The idea is to introduce randomness and break up the adversarial patterns.

2. **Adversarial Logit Pairing:** In this approach, adversarial examples are generated using the Fast Gradient Sign Method (FGSM), and the model is trained to minimize the difference between the logits (pre-softmax outputs) of clean examples and their corresponding adversarial examples. This encourages the model to have similar predictions for clean and adversarial inputs.

3. **Differential Privacy:** Differential privacy is a technique that adds controlled noise to the input data to protect the privacy of individual examples. In the context of adversarial defense, adding noise can help mitigate the impact of adversarial perturbations by making them less effective.


### Input Transformation Defense Mechanism Using Image Quilting Approach 

| **Compounded Attack** | **Pre-Attack Accuracy - No Defense** | **Post Attack Accuracy - No Defense** | **Post Attack Accuracy - with Defense** |
|------------------|------------------|------------------|--------------------|
| FGSM + CW        | 100.0%           | 22.0%           | 100.0%             |
| FGSM + PGD       | 100.0%           | 23.0%           | 100.0%             |
| CW + PGD         | 100.0%           | 98.0%           | 100.0%             |


### Input Transformation Defense Mechanism Using Adversarial Logit Pairing Approach 

| **Compounded Attack** | **Pre-Attack Accuracy - No Defense** | **Post Attack Accuracy - No Defense** | **Post Attack Accuracy - with Defense** |
|------------------|------------------|------------------|--------------------|
| FGSM + CW        | 100.0%           | 11.0%           | 100.0%             |
| FGSM + PGD       | 100.0%           | 20.0%           | 100.0%             |
| CW + PGD         | 100.0%           | 98.0%           | 100.0%             |

### Randomization Defense

Randomization defense techniques involve applying random transformations to the input data during training to increase the model's robustness against adversarial attacks. The key idea behind randomization defense is to introduce random variations in the input data, making it harder for adversarial perturbations to have a consistent effect on the model's predictions.

The implemented randomization defense methods work as follows:

- Random Resizing: The input images are randomly resized within a specified scale range. This introduces variations in the spatial dimensions of the images, making the model more resilient to size-related adversarial perturbations.
- Random Cropping: A random smaller region is cropped from the input images. This helps the model learn to focus on different parts of the image and reduces its sensitivity to specific pixel locations.
- Random Rotation: The input images are randomly rotated within a specified angle range. This helps the model become invariant to rotational changes and enhances its ability to recognize objects from different orientations.
- Combined Randomization: Multiple randomization techniques, including resizing, cropping, rotation, color jittering, random erasing, and noise injection, are applied together. This creates a diverse set of input variations, making it challenging for adversarial perturbations to have a consistent impact.

By applying these randomization techniques, the model learns to be more robust and generalizable, as it is trained on a wide range of input variations. Adversarial perturbations that are crafted based on a specific input may not have the same effect when random transformations are applied, reducing the effectiveness of adversarial attacks.

### Randomization Defense Mechanism Using Random Resizing Approach 

| **Compounded Attack** | **Pre-Attack Accuracy - No Defense** | **Post Attack Accuracy - No Defense** | **Post Attack Accuracy - with Defense** |
|------------------|------------------|------------------|--------------------|
| FGSM + CW        | 98.0%           | 6.0%           | 100.0%             |
| FGSM + PGD       | 100.0%           | 14.0%           | 100.0%             |
| CW + PGD         | 100.0%           | 98.0%           | 95.0%             |


### Randomization Defense Mechanism Using Random Cropping Approach 

| **Compounded Attack** | **Pre-Attack Accuracy - No Defense** | **Post Attack Accuracy - No Defense** | **Post Attack Accuracy - with Defense** |
|------------------|------------------|------------------|--------------------|
| FGSM + CW        | 100.0%           | 14.0%           | 100.0%             |
| FGSM + PGD       | 100.0%           | 27.0%           | 97.0%             |
| CW + PGD         | 100.0%           | 98.0%           | 100.0%             |


### Randomization Defense Mechanism Using Random Rotation Approach 

| **Compounded Attack** | **Pre-Attack Accuracy - No Defense** | **Post Attack Accuracy - No Defense** | **Post Attack Accuracy - with Defense** |
|------------------|------------------|------------------|--------------------|
| FGSM + CW        | 100.0%           | 11.0%           | 100.0%             |
| FGSM + PGD       | 100.0%           | 23.0%           | 100.0%             |
| CW + PGD         | 100.0%           | 98.0%           | 100.0%             |


### Randomization Defense Mechanism Using Combined Randomization Approach 

| **Compounded Attack** | **Pre-Attack Accuracy - No Defense** | **Post Attack Accuracy - No Defense** | **Post Attack Accuracy - with Defense** |
|------------------|------------------|------------------|--------------------|
| FGSM + CW        | 100.0%           | 16.0%           | 100.0%             |
| FGSM + PGD       | 100.0%           | 6.0%           | 100.0%             |
| CW + PGD         | 100.0%           | 97.0%           | 100.0%             |


### Adversarial Training Defense

Adversarial training is a defense technique that involves training the model on a combination of clean examples and adversarial examples generated using various attack methods. By exposing the model to adversarial examples during training, it learns to be more robust and resistant to adversarial perturbations.


### Adversarial Training Defense Mechanism

| **Compounded Attack** | **Pre-Attack Accuracy - No Defense** | **Post Attack Accuracy - No Defense** | **Post Attack Accuracy - with Defense** |
|------------------|------------------|------------------|--------------------|
| FGSM + CW        | 98.0%           | 20.0%           | 100.0%             |
| FGSM + PGD       | 98.0%           | 20.0%           | 98.0%             |
| CW + PGD         | 100.0%           | 89.0%           | 100.0%             |


## Importance of Adversarial Defense
Adversarial attacks pose a significant challenge to the reliability and trustworthiness of machine learning models. In real-world applications, the consequences of a model being deceived by adversarial examples can be severe. For example:

- In autonomous vehicles, an adversarial attack could cause the vehicle to misinterpret traffic signs or obstacles, leading to accidents.
- In medical diagnosis, an adversarial attack could manipulate medical images, causing misdiagnosis and incorrect treatment decisions.
- In cybersecurity, adversarial attacks could bypass security systems that rely on machine learning, allowing malicious activities to go undetected.

Therefore, it is crucial to develop and incorporate effective defense mechanisms into machine learning models. By making models more robust and resilient against adversarial attacks, we can increase their reliability and trustworthiness, enabling their safe and successful deployment in critical applications.

This project aims to contribute to the field of adversarial defense by exploring various techniques and providing an implementation of a defended Hybrid Neural Network. By combining classical and quantum computing approaches and incorporating defenses such as input transformation, adversarial training, and randomization, this project seeks to enhance the robustness of machine learning models against adversarial attacks.

## Further Reading: An Adversarial Attack Threat
Adversarial attacks pose a significant threat to machine learning models, particularly in critical applications such as autonomous vehicles, medical diagnosis, and cybersecurity. These attacks involve crafting malicious inputs that can deceive a model into making incorrect predictions, potentially leading to severe consequences. Therefore, it is crucial to incorporate defenses into models to make them more robust and resilient against adversarial attacks.

This project explores various defense techniques to protect a Hybrid Neural Network (HNN) against adversarial attacks. The HNN combines the strengths of classical and quantum computing by integrating a Convolutional Neural Network (CNN) with a Quantum Neural Network (QNN). The defenses implemented in this project include input transformation, adversarial training, and randomization.

## White-Box Targeted Compounded Adversarial Attacks
In the context of adversarial attacks against neural networks, white-box targeted compounded attacks are a particularly challenging and potent type of attack. Here's an explanation of these attacks and the motivation behind their use:

- **White-Box Attacks:** In a white-box attack scenario, the attacker has complete knowledge of the target model, including its architecture, parameters, and training data. This allows the attacker to craft highly effective adversarial examples by exploiting the model's vulnerabilities and inner workings.

- **Targeted Attacks:** Targeted attacks aim to manipulate the model's prediction towards a specific target class. Instead of simply causing misclassification, the attacker's goal is to force the model to predict a particular desired output. For example, in an image classification task, a targeted attack could aim to make the model misclassify a stop sign as a speed limit sign.

- **Compounded Attacks:** Compounded attacks involve the combination of multiple adversarial attack techniques to create more robust and effective adversarial examples. By leveraging the strengths of different attack methods, compounded attacks can generate adversarial examples that are more difficult to defend against.

The motivation behind using white-box targeted compounded attacks against classification neural networks, including hybrid neural networks, is as follows:

1. **Exploiting Model Vulnerabilities:** White-box access allows attackers to identify and exploit specific vulnerabilities in the model's architecture or learning process. By understanding the model's internal workings, attackers can craft adversarial examples that are tailored to the model's weaknesses, making them more effective.

2. **Targeted Misclassification:** Targeted attacks are particularly concerning because they can cause the model to make specific incorrect predictions chosen by the attacker. This can have severe consequences in applications where the cost of misclassification is high. For example, in a self-driving car, an attacker could target the model to misclassify a pedestrian as a road sign, leading to dangerous actions.

3. **Evading Defenses:** Compounded attacks combine multiple attack techniques, making them more robust against defensive mechanisms. By leveraging the strengths of different attack methods, compounded attacks can generate adversarial examples that are more difficult to detect and mitigate. This poses a significant challenge for defending models, including hybrid neural networks that incorporate quantum components.

4. **Testing Model Robustness:** White-box targeted compounded attacks serve as a rigorous test of a model's robustness and resilience. By subjecting the model to these powerful attacks, researchers can assess its vulnerability and develop effective defense strategies. This helps in identifying weaknesses and improving the overall security of the model.

In the case of hybrid neural networks, which combine classical and quantum components, white-box targeted compounded attacks can exploit the unique properties and vulnerabilities introduced by the quantum elements. Attackers may target the quantum circuits or the interface between the classical and quantum components to create adversarial examples that are specifically designed to deceive the hybrid model.

Defending against white-box targeted compounded attacks requires a multi-faceted approach that combines various defense techniques. This project implements defenses such as input transformation, adversarial training, and randomization to enhance the robustness of the hybrid neural network against these powerful attacks.

## Disclaimer
This code is for the purpose of education and research only. 
