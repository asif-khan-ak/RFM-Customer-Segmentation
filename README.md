# RFM Customer Segmentation 📊

This project implements **RFM Analysis (Recency, Frequency, Monetary)** on the UCI Online Retail dataset to segment customers and derive actionable insights, inspired by the YouTube tutorial video (timestamp ~0:49) you referenced.

## 📂 Dataset  
- **Name:** UCI Online Retail dataset  
- **Link:** `https://archive.ics.uci.edu/static/public/352/online+retail.zip`  
- Contains transactional data including InvoiceNo, InvoiceDate, CustomerID, Quantity, UnitPrice, Country, etc.

## 🧪 Project Steps

### 1. Data Loading & Pre‑processing  
- Load dataset, parse dates.  
- Drop entries with missing `CustomerID`.  
- Clean out negative quantities or refund records.  
- Remove non-sales items (e.g. POSTAGE, DISCOUNT) as described in Analytics Vidhya :contentReference[oaicite:1]{index=1}.

### 2. RFM Feature Engineering  
Using reference date = last invoice date + 1 day:
- **Recency:** Days since last purchase per customer  
- **Frequency:** Count of unique invoices per customer  
- **Monetary:** Sum of `Quantity × UnitPrice` per customer :contentReference[oaicite:2]{index=2}

### 3. Scoring & Segmenting  
- Use quantiles (`pd.qcut`) to bin Recency, Frequency, Monetary into quartiles (score 1–4), or a 1–5 scale if preferred :contentReference[oaicite:3]{index=3}.  
- Combine scores into composite RFM code or aggregate RFM score.  
- Optionally map to named segments like “Champions”, “Loyal”, “At Risk”, etc., based on score patterns :contentReference[oaicite:4]{index=4}.

### 4. Clustering (Optional)  
- Apply K‑Means (or GMM/DBSCAN) to RFM features.  
- Determine optimal cluster count (e.g. via silhouette score).  
- Visualize clusters in 3D (Recency vs Frequency vs Monetary) using Plotly or Seaborn :contentReference[oaicite:5]{index=5}.  
- Compute cluster vs population averages and “relative importance” metrics :contentReference[oaicite:6]{index=6}.

### 5. Insights & Strategy  
- Interpret each segment or cluster:
    - **New / Recent customers:** High recency, low frequency & spend  
    - **At risk / churned:** Old recency, low activity  
    - **Loyal / high value:** Low recency, high frequency & spending  
- Share recommendations: e.g. treat top segments with loyalty programs, re‑engage dormant ones, cross‑sell frequent mid‑spenders.

## 🧰 Technologies Used  
- Python (pandas, numpy, matplotlib / seaborn, plotly)  
- Google Colab Notebook for walkthrough  
- (Optional) scikit‑learn for clustering  
