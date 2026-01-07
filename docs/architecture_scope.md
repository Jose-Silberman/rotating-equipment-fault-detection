# Technical Stack and Project Scope

## Cloud Platform
Azure is selected as the reference cloud platform due to its widespread adoption in industrial and oil & gas environments, and its strong integration with data, ML, and governance services.

## Processing Mode
The system is designed primarily for batch processing:
- Periodic ingestion of time series data
- Scheduled model training
- Batch inference for health monitoring

Real-time streaming and low-latency inference are explicitly out of scope for the initial version.

## Data Storage
- Raw and processed data stored in parquet format
- Historian-like schema for time series data
- Data Lake–style storage abstraction

## Machine Learning Framework
- Python-based implementation
- Simple, interpretable anomaly detection models
- Focus on reproducibility rather than model complexity

## MLOps Components in Scope
- Reproducible training pipelines
- Experiment tracking
- Model registry
- Batch inference pipelines
- Data and model monitoring

## Explicitly Out of Scope
- Real-time SCADA integration
- Online learning
- Edge deployment
- Highly complex deep learning models
