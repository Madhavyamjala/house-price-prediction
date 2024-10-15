# House Price Prediction Model

This project is a comprehensive machine learning solution that predicts house prices based on various features. The project follows MLOps principles, including CI/CD pipelines, experiment tracking, and orchestration, to ensure efficient and reproducible workflows. It also implements software design patterns to make the codebase scalable and maintainable.

## Features
- **Machine Learning**: Implements various ML algorithms for house price prediction.
- **MLOps Integration**: Includes CI/CD pipelines for continuous model development and deployment.
- **Experiment Tracking**: Utilizes MLflow to track experiments, models, and hyperparameters.
- **Pipeline Orchestration**: ZenML is used to orchestrate and deploy ML pipelines.
- **Design Patterns**: The code follows best practices and design patterns to ensure modularity and scalability.

## Tech Stack
- **Python 3.8+**
- **MLflow**: For experiment tracking.
- **ZenML**: For pipeline orchestration and model deployment.
- **Pandas, Scikit-learn**: For data preprocessing and model development.
- **TensorFlow**: For deep learning models.
- **Flask**: (Optional) For serving the model as a web service.
- **Docker & Kubernetes**: (Optional) For containerization and deployment at scale.

## Installation and Setup

### Prerequisites
- Python 3.8+
- Git
- Virtual environment tools (`venv` or `virtualenv`)
- ZenML and MLflow integrations

### Step-by-Step Setup

1. **Clone the Repository**

   First, clone the project repository from GitHub:

   ```bash
   git clone https://github.com/Madhavyamjala/house-price-prediction.git
   cd house-price-prediction
   ```

2. **Create a Virtual Environment**

   Follow this guide to create a virtual environment: [Create Virtual Environment Guide](https://youtu.be/GZbeL5AcTgw?si=uj7B8-10kbyEytKo)

   Once the virtual environment is activated:

   ```bash
   source venv/bin/activate  # For Linux/macOS
   venv\Scripts\activate     # For Windows
   ```

3. **Install Required Dependencies**

   Install all necessary Python libraries and dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. **Install ZenML and MLflow Integrations**

   The project uses ZenML for pipeline orchestration and MLflow for tracking experiments. Install the necessary integrations:

   ```bash
   zenml integration install mlflow -y
   ```

5. **Configure the ZenML Stack**

   You need to configure the ZenML stack with the experiment tracker and model deployer:

   ```bash
   zenml experiment-tracker register mlflow_tracker --flavor=mlflow
   zenml model-deployer register mlflow --flavor=mlflow
   zenml stack register local-mlflow-stack -a default -o default -d mlflow -e mlflow_tracker --set
   ```

6. **Run the ZenML Pipeline**

   To execute the ML pipeline, use the `run_pipeline.py` script:

   ```bash
   python run_pipeline.py
   ```

7. **Deploy the Model**

   If you'd like to deploy the model, use the `run_deployment.py` script:

   ```bash
   python run_deployment.py
   ```

## Project Structure

```bash
├── analysis            # Scripts and notebooks for data analysis
├── data                # Raw and processed dataset files
├── explanations        # Explanatory documentation or data insights
├── extracted_data      # Extracted data from preprocessing steps
├── mlruns              # MLflow run tracking artifacts
├── pipelines           # ZenML pipelines for the project
├── src                 # Source code for the model and utilities
├── steps               # Individual steps in the ZenML pipeline
├── tests               # Unit and integration tests for the codebase
├── config.yaml         # Configuration file for the project
├── requirements.txt    # Python dependencies
├── run_deployment.py   # Script for deploying the model
├── run_pipeline.py     # Script for running the ZenML pipeline
├── sample_predict.py   # Script for running a sample prediction
```

## Experiment Tracking with MLflow

All experiments are tracked using MLflow, which logs:
- Model artifacts
- Hyperparameters
- Performance metrics (e.g., accuracy, loss)

You can visualize the experiment results using the MLflow UI:

```bash
mlflow ui
```

## Orchestrating Pipelines with ZenML

ZenML orchestrates the ML pipelines and handles tasks such as data ingestion, training, evaluation, and deployment. You can modify the steps of the pipeline inside the `pipelines` and `steps` directories.

## Testing

Unit tests and integration tests are available in the `tests` folder. To run the tests, use the following command:

```bash
pytest tests/
```

## Contributing

Feel free to fork this repository and submit a pull request if you'd like to contribute. All contributions are welcome.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
