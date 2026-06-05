# Diabetes Predictor

Diabetes Predictor is a machine learning project that predicts whether a person is likely to have diabetes based on common health measurements. The project includes a training script, a saved machine learning model, the diabetes dataset, and a Streamlit web app for making predictions through a simple browser interface.

> Note: This project is for learning and demonstration purposes only. It should not be used as a substitute for professional medical advice, diagnosis, or treatment.

## Features

- Predicts diabetes outcome using eight health-related inputs.
- Uses a Support Vector Machine classifier with a linear kernel.
- Includes a pre-trained model file: `trained_model.sav`.
- Provides a Streamlit web interface for entering patient data.
- Includes the dataset used for training and testing.

## Project Structure

```text
Diabetes-predictor-master/
|-- diabetes Prediction web app.py   # Streamlit web application
|-- project.py                       # Model training and testing script
|-- diabetes.csv                     # Diabetes dataset
|-- trained_model.sav                # Saved trained model
|-- Requirements.txt                 # Dependency file
|-- link.txt                         # Google Colab notebook link
`-- README.md                        # Project documentation
```

## Dataset

The project uses `diabetes.csv`, which contains the following input columns:

- `Pregnancies`
- `Glucose`
- `BloodPressure`
- `SkinThickness`
- `Insulin`
- `BMI`
- `DiabetesPedigreeFunction`
- `Age`

The target column is:

- `Outcome` - `0` means not diabetic, and `1` means diabetic.

## Technologies Used

- Python
- NumPy
- Pandas
- Scikit-learn
- Streamlit
- Pickle

## Setup

1. Clone or download this repository.

2. Open a terminal in the project folder:

   ```bash
   cd Diabetes-predictor-master
   ```

3. Create and activate a virtual environment.

   Windows:

   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   ```

   macOS/Linux:

   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```

4. Install the required packages:

   ```bash
   pip install numpy pandas scikit-learn streamlit
   ```

   The current `Requirements.txt` file is empty, so the packages above should be installed manually or added to that file.

## Running the Streamlit App

The Streamlit app is in `diabetes Prediction web app.py`.

Run it with:

```bash
streamlit run "diabetes Prediction web app.py"
```

Then open the local URL shown in the terminal, usually:

```text
http://localhost:8501
```

## Important Model Path Note

The Streamlit app currently loads the trained model from an absolute path:

```python
pickle.load(open('C:\\Users\\Gunjan\\OneDrive\\Desktop\\diabetes prediction miniproject\\mini project sem4\\trained_model.sav', 'rb'))
```

If you run the app on another computer, update that line to load the model from the project folder:

```python
loaded_model = pickle.load(open('trained_model.sav', 'rb'))
```

Make sure `trained_model.sav` is in the same folder as the Streamlit app.

## Training the Model

The training code is in `project.py`. It:

1. Loads the diabetes dataset.
2. Splits the data into training and testing sets.
3. Trains a linear Support Vector Machine classifier.
4. Checks training and testing accuracy.
5. Saves the trained model as `trained_model.sav`.

The script was originally written for Google Colab and contains:

```python
from google.colab import drive
drive.mount('/content/drive')
diabetes_dataset = pd.read_csv('/content/diabetes.csv')
```

To run it locally, replace the dataset path with:

```python
diabetes_dataset = pd.read_csv('diabetes.csv')
```

Then run:

```bash
python project.py
```

## Input Format

The model expects values in this order:

```text
Pregnancies, Glucose, BloodPressure, SkinThickness, Insulin, BMI, DiabetesPedigreeFunction, Age
```

Example:

```python
input_data = (5, 166, 72, 19, 175, 25.8, 0.587, 51)
```

## Output

The prediction result is one of:

- `The person is not diabetic`
- `The person is diabetic`

## Troubleshooting

- If Streamlit cannot find the model, check that `trained_model.sav` exists in the same folder as the web app and that the model path has been updated.
- If a package import fails, install the missing package with `pip install package-name`.
- If the training script fails locally because of `google.colab`, remove the Colab drive mounting lines and use the local dataset path.

## Future Improvements

- Add dependencies to `Requirements.txt`.
- Use number inputs in Streamlit instead of text inputs.
- Add input validation ranges for medical values.
- Display model accuracy in the app.
- Improve model performance with feature scaling and model comparison.
