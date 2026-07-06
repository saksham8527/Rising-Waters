{% extends 'base.html' %}
{% set active_page = 'about' %}

{% block content %}
<div class="about-page-container">
    <!-- Page Header -->
    <section class="about-header">
        <h1>Model Analysis & Pipeline Insights</h1>
        <p>Detailed performance benchmarks, feature importances, and exploratory data visualizations compiled during model training.</p>
    </section>

    <!-- Model Comparison Metrics Cards -->
    <section class="metrics-dashboard">
        <div class="metrics-grid-title">
            <h3>Active Classifier Benchmarks: <span class="gradient-text">{{ best_model_name }}</span></h3>
            <span class="active-badge"><i class="fa-solid fa-circle-check"></i> Primary Engine</span>
        </div>
        
        <div class="dashboard-stats-grid mini-stats">
            <div class="stats-card glass">
                <span class="stats-title">Classification Accuracy</span>
                <div class="stats-value text-accent">{{ best_model_metrics.accuracy * 100 }}%</div>
                <p class="stats-desc">Overall correct predictions on test split</p>
            </div>
            
            <div class="stats-card glass">
                <span class="stats-title">F1-Score</span>
                <div class="stats-value text-accent">{{ best_model_metrics.f1_score }}</div>
                <p class="stats-desc">Harmonic mean of Precision & Recall</p>
            </div>

            <div class="stats-card glass">
                <span class="stats-title">Precision Index</span>
                <div class="stats-value text-accent">{{ best_model_metrics.precision * 100 }}%</div>
                <p class="stats-desc">Reliability index of positive predictions</p>
            </div>

            <div class="stats-card glass">
                <span class="stats-title">Recall Rate</span>
                <div class="stats-value text-accent">{{ best_model_metrics.recall * 100 }}%</div>
                <p class="stats-desc">Ratio of actual floods successfully detected</p>
            </div>
        </div>
    </section>

    <!-- Visual Analysis Segment -->
    <section class="visuals-section">
        <h2>Exploratory Data Analysis & Performance Visuals</h2>
        <p class="visuals-intro">These plots were generated during the training phase from the underlying 5,000 meteorological records.</p>
        
        <!-- Plot Carousel / Grid -->
        <div class="plots-grid">
            <div class="plot-card glass">
                <div class="plot-header">
                    <h4>Model Performance Comparison</h4>
                    <p>Scored across accuracy, precision, recall, and F1 on a stratifying 80:20 validation split.</p>
                </div>
                <div class="plot-img-container">
                    <img src="{{ url_for('static', filename='images/plots/model_comparison.png') }}" alt="Model Performance Comparison Chart">
                </div>
            </div>

            <div class="plot-card glass">
                <div class="plot-header">
                    <h4>Relative Feature Importance</h4>
                    <p>Weight variables determined by the Random Forest classifier to establish decision nodes.</p>
                </div>
                <div class="plot-img-container">
                    <img src="{{ url_for('static', filename='images/plots/feature_importance.png') }}" alt="Feature Importance Chart">
                </div>
            </div>

            <div class="plot-card glass">
                <div class="plot-header">
                    <h4>Meteorological Correlation Heatmap</h4>
                    <p>Heatmap mapping linear correlation coefficients between raw atmospheric and hydrological telemetry.</p>
                </div>
                <div class="plot-img-container">
                    <img src="{{ url_for('static', filename='images/plots/correlation.png') }}" alt="Correlation Heatmap">
                </div>
            </div>

            <div class="plot-card glass">
                <div class="plot-header">
                    <h4>Seasonal Rainfall Density Split</h4>
                    <p>Distribution curve displaying precipitation volume ranges and corresponding flood flags.</p>
                </div>
                <div class="plot-img-container">
                    <img src="{{ url_for('static', filename='images/plots/distribution_plot.png') }}" alt="Rainfall Distribution Chart">
                </div>
            </div>
        </div>
    </section>

    <!-- Models Methodology -->
    <section class="methodology-section glass">
        <h2>Mathematical Models Compared</h2>
        <div class="models-info-grid">
            <div class="model-info-block">
                <h3><i class="fa-solid fa-tree"></i> Decision Tree</h3>
                <p>Splits data iteratively based on Gini Impurity reduction. Highly readable and maps clear weather threshold bounds, though susceptible to overfitting on small variances.</p>
            </div>
            
            <div class="model-info-block">
                <h3><i class="fa-solid fa-cubes"></i> Random Forest</h3>
                <p>Ensemble classifier combining numerous randomized decision trees. Prevents overfitting via bootstrap bagging, yielding superb precision when predicting across high-dimensional weather metrics.</p>
            </div>
            
            <div class="model-info-block">
                <h3><i class="fa-solid fa-arrows-to-dot"></i> K-Nearest Neighbors (KNN)</h3>
                <p>Classifies instances according to distance metrics (Euclidean) relative to surrounding neighbors. Excellent at picking up cluster anomalies like sudden low-pressure spikes.</p>
            </div>
            
            <div class="model-info-block">
                <h3><i class="fa-solid fa-gauge-high"></i> XGBoost</h3>
                <p>Extreme Gradient Boosting tree model. Trains sequential models to minimize residual errors. Renowned for top-tier execution speed and predictive performance on structured tables.</p>
            </div>
        </div>
    </section>
</div>
{% endblock %}
