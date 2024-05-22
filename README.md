# Hybrid Neural Network with Adversarial with Three Defense Choices

This repository contains an implementation of a Hybrid Neural Network (HNN) that combines a Convolutional Neural Network (CNN) with a Quantum Neural Network (QNN) to classify handwritten digits from the MNIST dataset. The HNN is protected against adversarial attacks using various defense techniques, including input transformation, adversarial training, and randomization.

## Motivating Articles
J. C. Costa, T. Roxo, H. Proença and P. R. M. Inácio, "How Deep Learning Sees the World: A Survey on Adversarial Attacks & Defenses," in IEEE Access, vol. 12, pp. 61113-61136, 2024, doi: 10.1109/ACCESS.2024.3395118. https://ieeexplore.ieee.org/abstract/document/10510296

## An Adversarial Attack Threat
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

## Defenses

### Input Transformation
Input transformation is a defense technique that aims to preprocess the input data before feeding it into the model. The goal is to make the input more robust and less susceptible to adversarial perturbations. This project implements three input transformation approaches:

1. **Image Quilting:** This technique involves dividing the input image into smaller patches and randomly replacing some of the patches with patches from clean images. The idea is to introduce randomness and break up the adversarial patterns.

2. **Adversarial Logit Pairing:** In this approach, adversarial examples are generated using the Fast Gradient Sign Method (FGSM), and the model is trained to minimize the difference between the logits (pre-softmax outputs) of clean examples and their corresponding adversarial examples. This encourages the model to have similar predictions for clean and adversarial inputs.

3. **Differential Privacy:** Differential privacy is a technique that adds controlled noise to the input data to protect the privacy of individual examples. In the context of adversarial defense, adding noise can help mitigate the impact of adversarial perturbations by making them less effective.

### Randomization
Randomization is a defense technique that introduces random perturbations or transformations to the input data or the model itself. The idea is to make the model's predictions less sensitive to small adversarial perturbations. This project implements several randomization approaches:

1. **Random Resizing and Padding:** The input images are randomly resized and padded before being fed into the model. This introduces spatial variability and makes it harder for adversarial perturbations to have a consistent effect.

2. **Random Cropping:** Random patches are cropped from the input images, reducing the impact of localized adversarial perturbations.

3. **Random Rotation:** The input images are randomly rotated within a certain range, making the model more invariant to rotational changes.

### Adversarial Training
Adversarial training is a defense technique that involves training the model with adversarial examples alongside clean examples. By exposing the model to adversarial examples during training, it learns to classify them correctly and becomes more robust against adversarial attacks.

In this project, adversarial examples are generated using various attack methods, such as the Fast Gradient Sign Method (FGSM), Projected Gradient Descent (PGD), and Carlini & Wagner (C&W) attack. The model is then trained with a combination of clean and adversarial examples to improve its resilience.

## Importance of Adversarial Defense
Adversarial attacks pose a significant challenge to the reliability and trustworthiness of machine learning models. In real-world applications, the consequences of a model being deceived by adversarial examples can be severe. For example:

- In autonomous vehicles, an adversarial attack could cause the vehicle to misinterpret traffic signs or obstacles, leading to accidents.
- In medical diagnosis, an adversarial attack could manipulate medical images, causing misdiagnosis and incorrect treatment decisions.
- In cybersecurity, adversarial attacks could bypass security systems that rely on machine learning, allowing malicious activities to go undetected.

Therefore, it is crucial to develop and incorporate effective defense mechanisms into machine learning models. By making models more robust and resilient against adversarial attacks, we can increase their reliability and trustworthiness, enabling their safe and successful deployment in critical applications.

This project aims to contribute to the field of adversarial defense by exploring various techniques and providing an implementation of a defended Hybrid Neural Network. By combining classical and quantum computing approaches and incorporating defenses such as input transformation, adversarial training, and randomization, this project seeks to enhance the robustness of machine learning models against adversarial attacks.

## Disclaimer
This code is for the purpose of education and research only. 
