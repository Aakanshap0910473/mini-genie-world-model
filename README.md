# 🎮 Mini-Genie: Action-Conditioned Neural World Model

An interactive foundation world model prototype inspired by **Google DeepMind's Genie** and **Decart's Oasis**, built using PyTorch.

Instead of running an explicit game engine with collision algorithms, this system renders an interactive 2D arcade environment entirely through neural network hallucinations conditioned on real-time user inputs.

---

## 🏗️ Architecture

1. **Visual Tokenizer (Conv-AE):**
   * Compresses 64x64x3 RGB frames into a compact 64-dimensional continuous latent space ($z_t$).
   * Designed without saturating non-linearities at the output layer to prevent gradient death on sparse backgrounds.

2. **Action Dynamics Model (Residual Transition Brain):**
   * An action-conditioned neural transition model that predicts the next latent vector:
     $$\hat{z}_{t+1} = z_t + \Delta(z_t, a_t)$$
   * Conditioned on discrete directional actions (Up, Down, Left, Right).

3. **Autoregressive Dream Engine:**
   * Receives an initial seed frame and user inputs.
   * Recursively imagines future states frame-by-frame purely from neural network weights.

---

## 🚀 How to Run

1. Open `Mini_Genie_World_Model.ipynb` in [Google Colab](https://colab.research.google.com/).
2. Select **Runtime > Change runtime type > T4 GPU**.
3. Run all cells (`Ctrl + F9`).
4. Use the interactive directional buttons to steer the player inside the hallucinated neural environment!

---

## 🛠️ Tech Stack
* **Language:** Python
* **Framework:** PyTorch, Torchvision
* **Compute:** NVIDIA T4 GPU (Google Colab)
* **Visuals & UI:** Matplotlib, ipywidgets
