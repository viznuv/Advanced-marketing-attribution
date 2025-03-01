# Advanced Marketing Attribution System


*A comprehensive marketing attribution system that implements multiple models from traditional to cutting-edge approaches, with data ingestion, processing, visualization, and reporting capabilities.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.7+](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/release/python-370/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=flat&logo=TensorFlow&logoColor=white)](https://www.tensorflow.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=flat&logo=Matplotlib&logoColor=black)](https://matplotlib.org/)
[![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=flat&logo=plotly&logoColor=white)](https://plotly.com/)

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [System Architecture](#system-architecture)
- [Installation](#installation)
- [Usage Guide](#usage-guide)
- [Data Requirements](#data-requirements)
- [Attribution Models](#attribution-models)
- [Visualizations](#visualizations)
- [Advanced Usage](#advanced-usage)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Overview

The Advanced Marketing Attribution System is a Python-based framework designed to help marketers and analysts understand the effectiveness of marketing channels across complex customer journeys. Unlike traditional single-touch attribution methods, this system allows for sophisticated multi-touch attribution analyses using a variety of models, from simple rule-based approaches to advanced machine learning techniques.

![Attribution Dashboard Example](./images/dashboard_example.png)

This system enables organizations to:

- Ingest and unify data from multiple marketing sources
- Map complete customer journeys across touchpoints
- Apply various attribution models to understand channel performance
- Visualize attribution results and customer journey patterns
- Generate comprehensive reports for stakeholders

## Key Features

### Data Ingestion and Processing

- **Multi-source Integration**: Connect to CSV files, APIs, SQL databases, and Google Analytics
- **Data Unification**: Combine data from different sources with customer identity resolution
- **Flexible Data Mapping**: Map fields and transformations between different data sources

### Customer Journey Mapping

- **Journey Sequencing**: Create chronological sequences of customer touchpoints
- **Funnel Stage Mapping**: Assign marketing funnel stages to different channels/touchpoints
- **Time Analysis**: Calculate time between touchpoints and total journey duration

![Customer Journey Example](./images/customer_journey_example.png)

### Attribution Modeling

- **Traditional Models**: First-touch, last-touch, linear, position-based, and time-decay
- **Advanced Models**: Markov chains, Shapley value, logistic regression
- **AI-based Models**: Deep learning with attention mechanisms
- **Model Comparison**: Side-by-side analysis of different attribution approaches

### Analytics and Visualization

- **Interactive Dashboards**: Comprehensive dashboards for attribution insights
- **Journey Visualization**: Sankey diagrams for customer flow analysis
- **Network Analysis**: Graph-based visualization of touchpoint interactions
- **Custom Reporting**: Automated HTML reports with key insights

![Attribution Comparison Example](./images/attribution_comparison_example.png)

### Advanced Capabilities

- **Causal Inference**: Uplift modeling and double ML for estimating causal impact
- **Customer Segmentation**: ML-based clustering of journey patterns
- **Budget Allocation**: RL-based recommendations for optimal channel spend
- **Performance Tracking**: Monitor attribution changes over time

## System Architecture

The system is built with a modular architecture, making it easy to extend and customize. Below is a high-level overview of the main components:

![System Architecture](./images/system_architecture.png)

### Core Components

1. **DataIngestion**: Handles data import from multiple sources
2. **CustomerJourney**: Creates and analyzes customer journey sequences
3. **AttributionModels**: Implements various attribution algorithms
4. **AdvancedAnalytics**: Provides advanced statistical and ML capabilities
5. **Visualization**: Creates visual representations of attribution results
6. **MarketingAttribution**: Main class that integrates all components

### Data Flow

1. Raw marketing data → DataIngestion → Unified customer data
2. Unified data → CustomerJourney → Journey sequences
3. Journey sequences → AttributionModels → Attribution results
4. Journey sequences → AdvancedAnalytics → Additional insights
5. All results → Visualization → Visual reports and dashboards

## Installation

### Prerequisites

- Python 3.7+
- pip package manager

### Dependencies

The system requires several Python libraries, including:

- numpy, pandas, scipy
- matplotlib, seaborn, plotly
- scikit-learn, tensorflow
- networkx, shap
- tqdm

### Installation Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/marketing-attribution.git
   cd marketing-attribution
   ```

2. Create and activate a virtual environment (recommended):
   ```bash
   python -m venv env
   # On Windows
   env\Scripts\activate
   # On macOS/Linux
   source env/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Verify installation:
   ```python
   python -c "from marketing_attribution import MarketingAttribution; print('Installation successful!')"
   ```

## Usage Guide

### Quick Start

The quickest way to get started is to use the provided example data:

```python
from marketing_attribution import MarketingAttribution
from marketing_attribution.utils import create_sample_data

# Generate sample data
sample_data = create_sample_data()

# Initialize the system
attribution_system = MarketingAttribution()

# Ingest sample data
attribution_system.data_ingestion.ingest_csv(
    name='website_analytics',
    file_path='sample_data/website_analytics.csv'
)
attribution_system.data_ingestion.ingest_csv(
    name='email_campaigns',
    file_path='sample_data/email_campaigns.csv'
)
attribution_system.data_ingestion.ingest_csv(
    name='paid_ads',
    file_path='sample_data/paid_ads.csv'
)

# Create customer journeys
unified_data = attribution_system.data_ingestion.unify_customer_data(
    id_mapping_columns={
        'website_analytics': 'user_id',
        'email_campaigns': 'email_id',
        'paid_ads': 'click_id'
    },
    timestamp_columns={
        'website_analytics': 'timestamp',
        'email_campaigns': 'date',
        'paid_ads': 'click_time'
    },
    conversion_column='purchase'
)

journeys = attribution_system.customer_journey.create_customer_journeys(
    customer_id_col='customer_id',
    timestamp_col='timestamp',
    channel_col='data_source',
    conversion_col='is_conversion'
)

# Run attribution models
attribution_results = attribution_system.run_attribution_models([
    'first_touch',
    'last_touch',
    'linear',
    'markov_chain'
])

# Create visualizations
attribution_system.create_visualizations(
    visualizations=['attribution_comparison', 'customer_journey'],
    output_dir='attribution_results'
)

# Generate report
attribution_system.generate_report(
    output_path='attribution_results/attribution_report.html'
)
```

### Running with Google Colab

The system can be easily run in Google Colab:

1. Create a new notebook at [Google Colab](https://colab.research.google.com/)
2. Install dependencies and import the required code
3. Upload your marketing data or use the provided sample data generator
4. Run the attribution analysis and visualize results

![Colab Example](./images/colab_example.png)

### Complete End-to-End Example

For a comprehensive example of using all features, refer to the `example_usage()` function in the source code or the [examples](./examples/) directory in the repository.

## Data Requirements

### Input Data Format

The system can work with various data formats, but the most common is CSV files. Each data source should contain:

1. **Customer Identifier**: A unique ID for each customer or user
2. **Timestamp**: When the interaction occurred
3. **Channel Information**: The marketing channel or touchpoint
4. **Conversion Data**: Whether a conversion occurred (optional, can be inferred)

### Example Data Structure

#### Website Analytics Data
```
user_id,timestamp,page_path,session_id,cost
cust_0001,2023-01-05 14:32:18,home,session_a1b2c3,0.0
cust_0002,2023-01-06 09:45:33,product,session_d4e5f6,0.0
```

#### Email Campaign Data
```
email_id,date,campaign_name,subject,cost
cust_0001,2023-01-07 10:15:22,newsletter,Special Offer,0.05
cust_0003,2023-01-08 16:45:02,promotion,New Products,0.05
```

#### Paid Ads Data
```
click_id,click_time,platform,campaign,cost,purchase
cust_0002,2023-01-09 11:22:33,google_ads,remarketing,0.75,0
cust_0003,2023-01-10 14:05:17,facebook_ads,acquisition,1.25,1
```

### Data Preparation

For optimal results:

- Ensure timestamps are in a consistent format
- Remove duplicate entries
- Handle missing values appropriately
- Ensure customer IDs are consistent across sources
- Normalize channel/touchpoint names

## Attribution Models

The system implements a variety of attribution models to suit different analysis needs:

### Traditional Models

| Model | Description | Best Use Case | Visualization |
|-------|-------------|---------------|---------------|
| **First Touch** | Attributes 100% credit to the first touchpoint | Understanding awareness/acquisition channels | ![First Touch](./images/first_touch_model.png) |
| **Last Touch** | Attributes 100% credit to the last touchpoint | Evaluating closing/conversion channels | ![Last Touch](./images/last_touch_model.png) |
| **Linear** | Distributes credit equally across all touchpoints | Balanced view when all touchpoints matter equally | ![Linear](./images/linear_model.png) |
| **Position-Based** | Weights first and last touchpoints higher (e.g., 40/20/40) | Emphasizing acquisition and conversion channels | ![Position-Based](./images/position_based_model.png) |
| **Time Decay** | Gives more credit to touchpoints closer to conversion | Recognizing recency importance | ![Time Decay](./images/time_decay_model.png) |

### Advanced Models

| Model | Description | Advantages | Visualization |
|-------|-------------|------------|---------------|
| **Markov Chain** | Uses probabilistic transitions between states | Considers path dependencies | ![Markov Chain](./images/markov_chain_model.png) |
| **Shapley Value** | Game theory approach for fair value distribution | Accounts for all possible combinations | ![Shapley Value](./images/shapley_value_model.png) |
| **Logistic Regression** | ML approach using conversion probability | Data-driven with statistical basis | ![Logistic Regression](./images/logistic_regression_model.png) |
| **Deep Learning** | Neural networks with attention mechanisms | Captures complex non-linear relationships | ![Deep Learning](./images/deep_learning_model.png) |

### Model Comparison

The system provides tools to compare attribution results across models:

```python
comparison = attribution_system.attribution_models.compare_models([
    'first_touch', 'last_touch', 'linear', 'markov_chain', 'shapley'
])
```

![Model Comparison](./images/model_comparison.png)

## Visualizations

The system provides several visualization types for different analytical needs:

### Attribution Comparison

Bar charts comparing attribution percentages across different models and channels.

```python
fig = attribution_system.visualization.plot_attribution_comparison()
```

![Attribution Comparison](./images/attribution_comparison_full.png)

### Customer Journey Sankey

Sankey diagrams showing the flow of customers through different touchpoints.

```python
fig = attribution_system.visualization.plot_customer_journey_sankey()
```

![Customer Journey Sankey](./images/customer_journey_sankey.png)

### Conversion Funnel

Funnel charts showing conversion rates across marketing funnel stages.

```python
fig = attribution_system.visualization.plot_conversion_funnel()
```

![Conversion Funnel](./images/conversion_funnel.png)

### Network Graph

Network visualization of touchpoint interactions and relationships.

```python
fig = attribution_system.visualization.plot_network_graph()
```

![Network Graph](./images/network_graph.png)

### Customer Segments

Scatter plots of customer segments based on journey patterns.

```python
fig = attribution_system.visualization.plot_customer_segments()
```

![Customer Segments](./images/customer_segments.png)

### Interactive Dashboard

Comprehensive dashboard combining multiple visualizations for a holistic view.

```python
fig = attribution_system.visualization.create_interactive_dashboard()
```

![Interactive Dashboard](./images/interactive_dashboard.png)

## Advanced Usage

### Customizing Attribution Models

You can customize parameters for various attribution models:

```python
# Custom position-based model with 30/40/30 weighting
position_results = attribution_system.attribution_models.run_position_based_attribution(
    first_weight=0.3,
    last_weight=0.3
)

# Time decay with custom half-life
time_decay_results = attribution_system.attribution_models.run_time_decay_attribution(
    half_life_days=14
)

# Shapley with limited combination size for performance
shapley_results = attribution_system.attribution_models.run_shapley_value_attribution(
    max_combination_size=3
)
```

### Advanced Analytics

The system provides several advanced analytical capabilities:

#### Uplift Modeling

```python
uplift_results = attribution_system.advanced_analytics.uplift_modeling(
    control_group_column='is_control'
)
```

![Uplift Model](./images/uplift_model.png)

#### Double ML for Causal Inference

```python
causal_results = attribution_system.advanced_analytics.double_ml_attribution(
    features=['age', 'gender', 'location', 'device_type']
)
```

![Causal Inference](./images/causal_inference.png)

#### Reinforcement Learning for Budget Allocation

```python
allocation_results = attribution_system.advanced_analytics.reinforcement_learning_allocation(
    budget=10000,
    channels=['google_ads', 'facebook_ads', 'email', 'organic_search', 'direct'],
    returns={'google_ads': 1.8, 'facebook_ads': 1.6, 'email': 2.2},
    volatility={'google_ads': 0.4, 'facebook_ads': 0.5, 'email': 0.3}
)
```

![Budget Allocation](./images/budget_allocation.png)

### Custom Data Integration

For more complex data sources, you can use the advanced integration features:

```python
# SQL database integration
attribution_system.data_ingestion.ingest_sql_data(
    name='crm_data',
    query='SELECT customer_id, interaction_date, channel, product_purchased FROM customer_interactions',
    connection_string='postgresql://username:password@hostname:port/database'
)

# API integration
attribution_system.data_ingestion.ingest_api_data(
    name='social_media',
    api_url='https://api.example.com/social-interactions',
    headers={'Authorization': 'Bearer YOUR_API_TOKEN'},
    params={'start_date': '2023-01-01', 'end_date': '2023-03-31'}
)

# Google Analytics integration
attribution_system.data_ingestion.ingest_google_analytics(
    name='ga_data',
    view_id='12345678',
    metrics=['ga:sessions', 'ga:transactions', 'ga:transactionRevenue'],
    dimensions=['ga:source', 'ga:medium', 'ga:campaign', 'ga:date'],
    start_date='2023-01-01',
    end_date='2023-03-31',
    credentials_path='ga_credentials.json'
)
```

## 🛠️ Troubleshooting

### Common Issues and Solutions

#### Customer Journey Creation Fails

**Problem**: Error `No data available for creating customer journeys`

**Solution**:
- Ensure unified data has required columns: `customer_id`, `timestamp`, `data_source`, `is_conversion`
- Check that timestamp is in datetime format
- Verify is_conversion is boolean type
- Use manual journey creation as a fallback:

```python
# Manual journey creation
journeys = manual_customer_journey_creation(unified_data)
fix_visualization_issues(attribution_system, journeys)
```

#### Visualization Errors

**Problem**: Error `Format 'html' is not supported`

**Solution**:
- For matplotlib-based visualizations, use .png format instead of .html:
```python
fig = attribution_system.visualization.plot_attribution_comparison(save_path='results/comparison.png')
```

#### Component Connection Issues

**Problem**: Components not properly connected, causing cascading errors

**Solution**:
- Apply the visualization fixes function to ensure all components are connected:
```python
fix_visualization_issues(attribution_system, journeys)
```

#### Memory Issues with Large Datasets

**Problem**: Out of memory errors with large datasets

**Solution**:
- Use chunking for data ingestion
- Limit the complexity of advanced models:
```python
# Limit Shapley combinations
shapley_results = attribution_system.attribution_models.run_shapley_value_attribution(
    max_combination_size=2
)
```

### Debugging Tips

1. Enable detailed logging:
   ```python
   import logging
   logging.basicConfig(level=logging.DEBUG)
   ```

2. Inspect data at each stage:
   ```python
   print(f"Unified data shape: {unified_data.shape}")
   print(f"Unified data columns: {unified_data.columns.tolist()}")
   print(f"Sample data:\n{unified_data.head()}")
   ```

3. Check data types:
   ```python
   print(unified_data.dtypes)
   ```

4. Verify timestamp formatting:
   ```python
   print(f"Timestamp type: {type(unified_data['timestamp'].iloc[0])}")
   ```

5. Use the diagnostic functions included in the utils:
   ```python
   from marketing_attribution.utils import debug_unified_data
   debug_unified_data(unified_data)
   ```

## 👥 Contributing

Contributions to the Marketing Attribution System are welcome! Here's how to contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Contribution Guidelines

- Follow the existing code style and conventions
- Add unit tests for new features
- Update documentation as needed
- Make sure all tests pass before submitting a PR

### Development Setup

```bash
# Clone the repository
git clone https://github.com/viznuv/marketing-attribution.git
cd marketing-attribution

# Create a virtual environment
python -m venv env
source env/bin/activate  # On Windows: env\Scripts\activate

# Run tests
pytest
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📮 Contact

For questions, feature requests, or issues, please use the GitHub issue tracker or contact the project maintainers:

- Email: vishnuprasad@sjmsom.in

---

*Made with ❤️ for marketers and data scientists who want to understand the true impact of their marketing efforts.*
