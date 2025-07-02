
# 🎭 Avatar-Based Talking Face Generation  
### Audio-Driven Emotional Avatars with Landmark and Head Motion Modeling

This repository presents a deep learning system that generates **emotionally expressive, speech-synchronized avatar videos** from a static face image and a speech audio clip. The system preserves identity, extracts emotions directly from audio, and outputs anime-style talking avatars using landmark motion and head orientation cues.

---

## 📌 Features

- 🖼️ Converts real human faces to anime-style avatars using TCN and GAN  
- 🔊 Extracts emotion features directly from raw speech audio  
- 🗣️ Produces realistic lip-sync and head movements with transformer-based modeling  
- 💡 Adds natural stochastic variations to improve expressiveness  
- 🔐 Prioritizes user privacy by not using actual human faces in generated videos

---

## 🛠️ Tech Stack

| Component               | Technologies Used                             |
|-------------------------|-----------------------------------------------|
| Programming Language    | Python                                        |
| Deep Learning Framework | PyTorch                                       |
| Audio Processing        | Librosa, Mel-Spectrogram                      |
| Face Detection          | Dlib, OpenCV                                  |
| Models Used             | U-Net, GAN, TCN, CNN-LSTM, Transformers       |
| Dataset Formats         | .hdf5 for processed frames and landmarks      |
| Training Losses         | Adversarial Loss, Perceptual Loss, MSE, LPIPS|
| Datasets                | CREMA-D, Face2Comics                          |

---

## 🧠 System Architecture

The pipeline includes 7 core modules:

1. **Preprocessing**  
   - Extracts frames, 68 facial landmarks, and normalized audio features.
2. **Face-to-Anime Translation**  
   - Converts real face images into anime-style avatars using U-Net + TCN.
3. **Speech Embedding**  
   - Transforms speech to feature embeddings using CNN + LSTM.
4. **Image Embedding**  
   - Captures speaker identity with ResNet-18 based encoder.
5. **Emotion Embedding**  
   - Automatically detects emotions from audio and encodes them.
6. **Noise Embedding**  
   - Adds natural variation for realistic generation.
7. **Video Frame Generation**  
   - Synthesizes emotion-aligned, speech-synced avatar video frames.

---

## 🧪 Datasets

- **CREMA-D**  
  > Audio-visual dataset with over 7,000 clips labeled with six emotions (angry, disgusted, fearful, happy, neutral, sad).  
  Used for training emotional and lip-sync alignment modules.

- **Face2Comics by Sxela**  
  > Paired dataset of real and anime-style faces.  
  Used for training the face-to-avatar stylization module.

---

 📈 Evaluation Metrics

| Metric      | Description |
|-------------|-------------|
| **MSE**     | Measures average squared error between frames. |
| **PSNR**    | Indicates video quality in decibels. |
| **SSIM**    | Structural similarity measure between frames. |
| **LPIPS**   | Learned perceptual similarity using deep features. |
| **Landmark Drift** | Euclidean distance between predicted and reference landmarks. |

 📊 Example Test Cases

| Test Case | Input | Expected Behavior |
|-----------|-------|-------------------|
| Valid face + audio | Frontal face + .wav | Generates video with synced lip & emotion |
| Side-profile | Side face image | Warning or fallback |
| No face detected | Empty image | Exception raised |
| No emotion detected | Flat audio | Generates neutral expression |
| Invalid format | .mp3 | Format error thrown |


