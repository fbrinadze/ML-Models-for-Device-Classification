# EndpointScanner ML Models

Pre-trained machine learning models for network device classification and anomaly detection.

## Models Included

| File | Description | Format |
|------|-------------|--------|
| device_classifier.pkl | Classifies network devices (Desktop, Laptop, Server, Printer, etc.) | scikit-learn pickle |
| os_fingerprint.pkl | Identifies operating systems from network signatures | scikit-learn pickle |
| anomaly_detector.pkl | Detects anomalous devices on the network | scikit-learn pickle |
| auto_labeler.pkl | Automatically labels devices using clustering | scikit-learn pickle |

## Training Data

| File | Description |
|------|-------------|
| 	raining_data.json | Device classification training samples |
| os_training.json | OS fingerprinting training samples |
| anomaly_baseline.json | Baseline data for anomaly detection |
| cluster_labels.json | Cluster-to-label mappings |

## Requirements

```
scikit-learn>=1.0.0
numpy>=1.20.0
```

## Usage

```python
import pickle

# Load device classifier
with open('device_classifier.pkl', 'rb') as f:
    classifier = pickle.load(f)

# Load OS fingerprinter
with open('os_fingerprint.pkl', 'rb') as f:
    os_fp = pickle.load(f)

# Load anomaly detector
with open('anomaly_detector.pkl', 'rb') as f:
    anomaly = pickle.load(f)
```

## Model Details

### Device Classifier
- **Algorithm**: Random Forest
- **Features**: Open ports, MAC vendor, TTL, hostname patterns
- **Classes**: Desktop, Laptop, Server, Printer, Network Device, Mobile Device, IoT Device, Unknown

### OS Fingerprinter
- **Algorithm**: Random Forest
- **Features**: TTL, open ports, service banners
- **Classes**: Windows 10/11, Windows Server, Linux, macOS, Network Device OS

### Anomaly Detector
- **Algorithm**: Isolation Forest
- **Purpose**: Identifies devices that don't match normal network patterns
- **Output**: Anomaly score (higher = more anomalous)

## License

MIT License - Free to use and modify.

