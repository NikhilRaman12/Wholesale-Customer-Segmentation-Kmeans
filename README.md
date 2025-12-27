\# Wholesale Customer Segmentation using K-Means



\## Overview



This project demonstrates an end-to-end machine learning workflow for customer segmentation using unsupervised learning. The goal is to cluster wholesale customers based on purchasing behavior, providing insights for marketing, product strategy, and business decision-making. The project is designed to be reproducible, containerized, and deployable on Kubernetes.



---



\## Project Workflow



\### 1. Data Acquisition

\- Dataset: `Wholesale customers data.csv` (UCI Machine Learning Repository).

\- Features: Fresh, Milk, Grocery, Frozen, Detergents\_Paper, Delicassen.

\- Target: None (unsupervised).



\### 2. Data Preprocessing

\- StandardScaler applied to normalize features.

\- Saved fitted scaler as `scaler.pkl`.



\### 3. Model Training

\- K-Means clustering applied to the dataset.

\- Optimal number of clusters determined using the elbow method.

\- Trained model saved as `kmeans.pkl`.



\### 4. Model Serving

\- `model.py` contains training and preprocessing logic.

\- `app.py` provides a Gradio interface for interactive predictions.

\- Input: Six numerical features.

\- Output: Cluster label with interpretation.



\### 5. Containerization

\- `Dockerfile` builds a reproducible environment for the app.

\- `.dockerignore` ensures lean image size.

\- Image tagged as `customer-segmentation`.



\### 6. Deployment

\- `deployment.yaml`: Kubernetes Deployment manifest.

\- `service.yaml`: Kubernetes Service manifest.

\- `k8s.yaml`: Combined manifest for quick deployment.

\- Supports NodePort or LoadBalancer for external access.



\### 7. Security

\- `certificate.pem` included for optional HTTPS support in Gradio.



---



\## Project Structure



```

customer\_segmentation/

├── .dockerignore

├── Dockerfile

├── app.py

├── model.py

├── kmeans.pkl

├── scaler.pkl

├── Wholesale customers data.csv

├── requirements.txt

├── deployment.yaml

├── service.yaml

├── k8s.yaml

├── certificate.pem

├── .gradio/

└── flagged/

```



---



\## Local Setup



```bash

\# Clone the repository

git clone https://github.com/NikhilRaman12/Wholesale-Customer-Segmentation-Kmeans.git

cd Wholesale-Customer-Segmentation-Kmeans/customer\_segmentation



\# Create and activate virtual environment

python -m venv venv

source venv/bin/activate   # Windows: venv\\Scripts\\activate



\# Install dependencies

pip install -r requirements.txt



\# Run the Gradio app

python app.py

```



---



\## Docker Deployment



```bash

\# Build Docker image

docker build -t customer-segmentation .



\# Run container

docker run -p 7860:7860 customer-segmentation

```



Access the app at `http://localhost:7860`.



---



\## Kubernetes Deployment



```bash

\# Apply combined manifest

kubectl apply -f k8s.yaml



\# OR apply separately

kubectl apply -f deployment.yaml

kubectl apply -f service.yaml

```



Access the app via NodePort or LoadBalancer depending on your cluster setup.



---



\## Reproducibility Notes



\- Dockerfile ensures consistent environment across machines.

\- Kubernetes manifests support scalable deployment.

\- Dependencies pinned in `requirements.txt`.

\- `.dockerignore` excludes unnecessary files from the image.



---



\## Contributing



Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.



---



\## License



This project is licensed under the MIT License.



---



\## Author



\*\*Nikhil Raman K\*\*  

AI/ML Engineer and Data Scientist  

Focused on agentic AI systems, reproducible demos, and recruiter-ready launches  

Location: Hyderabad, India  

GitHub: \[NikhilRaman12](https://github.com/NikhilRaman12)  

