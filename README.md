# Multi-Modal Biometric Identification System

## Overview
This project implements a secure human identification system using multi-modal biometrics (iris, fingerprint, and palmprint) based on the research paper:

**"Secure Human Identification with Multi-Modal Biometrics Using Weighted Jackal Optimization and Transformer-Based SqueezeNet"**

## System Architecture

The system achieves **99.64% accuracy** through the following pipeline:

1. **Preprocessing**: Guided Non-Local Filter (Equations 1-8)
2. **Feature Extraction**: SiaNet - Siamese CNN (Equations 9-12)
3. **Feature Fusion**: Parallel Maximum Covariance (Equations 13-16) 
4. **Optimization**: Weighted Jackal Optimization (Equations 17-26)
5. **Classification**: Transformer-based SqueezeNet (Equations 27-35)

## Project Structure

```
multimodal_biometric/
├── data/
│   ├── iris/
│   ├── fingerprint/
│   └── palmprint/
├── src/
│   ├── __init__.py
│   ├── preprocessing.py          # Guided Non-Local Filter
│   ├── feature_extraction.py    # SiaNet (Siamese CNN)
│   ├── feature_fusion.py        # Parallel Maximum Covariance
│   ├── optimization.py          # Weighted Jackal Optimization
│   ├── classifier.py            # Transformer-based SqueezeNet
│   └── utils.py                 # Helper functions
├── models/
│   └── saved_models/
├── train.py
├── evaluate.py
├── requirements.txt
└── README.md
```

## Installation

```bash
# Clone the repository
git clone https://github.com/gollaaravindkumar/Mulitmodal.git
cd Mulitmodal

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## Requirements

- Python 3.8+
- TensorFlow 2.10+
- OpenCV 4.5+
- NumPy, SciPy
- See requirements.txt for complete list

## Dataset

The system is designed to work with the **CASIA dataset**:
- Iris images: 619 samples
- Fingerprint images: 619 samples  
- Palmprint images: 619 samples
- Split: 495 training / 124 testing

## Usage

### Training

```bash
python train.py --data_path ./data --epochs 100 --batch_size 32
```

### Evaluation

```bash
python evaluate.py --model_path ./models/saved_models/best_model.h5
```

## Key Components

### 1. Guided Non-Local Filter
Hybrid preprocessing combining:
- Bilateral filtering
- Guided filtering  
- Non-local means filtering
- Z-score normalization

### 2. SiaNet Feature Extraction
- 4 hidden convolutional layers
- Exponential Linear Units (ELU) activation
- Feature-parallel pooling
- Contrastive loss function

### 3. Parallel Maximum Covariance Fusion
- Feature length equalization
- Covariance maximization
- Redundant feature removal

### 4. Weighted Jackal Optimization
- Nature-inspired optimization
- Golden jackal hunting behavior
- Feature selection based on fitness

### 5. Transformer-based SqueezeNet
- Multi-head attention mechanism
- Positional encoding
- Fire modules with squeeze/excitation
- Sigmoid output layer

## Performance

| Metric | Independent Run | 5-Fold CV | 10-Fold CV |
|--------|----------------|-----------|------------|
| Accuracy | 99.64% | 93.33% | 97.76% |
| EER | 0.41% | - | - |

## Implementation Status

- [x] requirements.txt
- [ ] src/preprocessing.py
- [ ] src/feature_extraction.py
- [ ] src/feature_fusion.py
- [ ] src/optimization.py
- [ ] src/classifier.py
- [ ] train.py
- [ ] evaluate.py

## Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## Citation

If you use this code, please cite:
```
Secure Human Identification with Multi-Modal Biometrics Using Weighted Jackal 
Optimization and Transformer-Based SqueezeNet
Vijay M, Edamakanti Ramanji Reddy, Golla Aravind Kumar, et al.
```

## License

MIT License

## Contact

For questions or collaboration:
- Email: gollaaravindkumar143@gmail.com
- GitHub: @gollaaravindkumar

## Acknowledgments

- CASIA Dataset
- Research team at Kalasalingam Academy of Research and Education
- TensorFlow and Keras communities
