**Quick Usage Guide**

```
project/
├─ datasets/                       # Place your data here
│  ├─ combined_datasets_whole/     # onset/apex images for landmark detection
│  ├─ STSNet_whole_norm_u_v_os/    # Full-frame optical flow (u, v, |∇|)
│  └─ three_norm_u_v_os/           # LOSO directory: sub_x/u_train | u_test/…
├─ model.py                        # Network architecture
├─ prepare_data.py                 # Data cropping & AU adjacency construction
├─ train.py                        # Training script
├─ test.py                         # Testing script
└─ requirements.txt
```

### Installation

```bash
pip install -r requirements.txt   # Install dependencies
pip install dlib                  # If not automatically installed
```

> ⚠️ Requires `mmod_human_face_detector.dat` and `shape_predictor_68_face_landmarks.dat` in the project root directory.

### Training

```bash
python train.py
```

* Performs LOSO training on each subject under `datasets/three_norm_u_v_os/`
* Saves the best model weights to `ourmodel_weights/<subject>.pth`

### Testing / Inference

```bash
python test.py
```

* Loads weights from `ourmodel_weights` and outputs per-subject classification reports

---

To adjust hyperparameters, edit the top section of `train.py`:

```python
epochs = 100
batch_size = 128
learning_rate = 5e-5
```
