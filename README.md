# Fine-Tuning VGG16 for Better Performance

## 👥 Team Members
* **Chao-Chung Liu** (Student ID: 9067679)
* **Emmanuel Chiebuka Ihejiamaizu** (Student ID: 9080005)
* **Liggia Elena Cruz** (Student ID: 9085905)

---

## 📖 Project Description
This project explores Transfer Learning and Fine-Tuning techniques using the pre-trained VGG16 model. We compared different optimization strategies to adapt a large-scale model to a specific "Cats vs. Dogs" binary classification task with a limited dataset.

---

## 📊 Dataset Description
* **Title:** Dogs vs. Cats (Kaggle Edition)
* **Source:** [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=54765)
* **Content:** 2,000 images for training, 1,000 for validation, and 2,000 for testing.
* **Preprocessing:** Preprocessing: Images resized to 180x180, normalized using VGG16's specific preprocessing pipeline, and filtered to remove corrupted files.

---

## 🛠️ Experimental Setup (The Three Runs)
To ensure a fair comparison, all experiments started from the same Task 1 Baseline (97.6% accuracy).
1. Feature Extraction Baseline (Task 1): Training only the custom top classifier while keeping VGG16 frozen.
2. Running A (Manual Fine-Tuning): Unfreezing Block 5 of VGG16 and retraining with a fixed low learning rate ($1 \times 10^{-5}$).
3. Running B (Aggressive Scheduler): Starting fine-tuning with a high learning rate ($1 \times 10^{-3}$) combined with `ReduceLROnPlateau`.
4. Running C (Conservative Scheduler): Starting with a safe learning rate ($1 \times 10^{-5}$) and using a scheduler for precise optimization.

---

## 🧭 Key Conclusions
Our experiments yielded significant insights into Deep Learning dynamics:
* Catastrophic Forgetting: Running B failed (dropped to 50% accuracy) because the high learning rate destroyed the pre-trained weights in the convolutional base.
* Performance Ceiling: Given the small dataset, accuracy plateaued at 97.6%. However, fine-tuning in Running C successfully refined the Validation Loss (from 0.3420 to 0.3388).
* Best Practice: The most robust strategy for fine-tuning is starting with a very low learning rate and employing an automated scheduler to prevent divergence.

---

## 🚀 How to Run
1. Clone this repository.
```bash
https://github.com/caatat741213/ConvolutionalNeuralNetworks.git
```

2.Set up the Environment:
```bash
python -m venv venv
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate
```

3.Install dependencies:
```bash
pip install -r requirements.txt
```

4.Dataset Preparation:
* Download the dataset[Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=54765)
* Unzip the file.
* Create the directory structure: data/kaggle_dogs_vs_cats/train.

5.Run the Notebook:

Open Fine_Tuning_VGG16_Workshop.ipynb in VS Code or Jupyter Notebook and run the cells sequentially.
