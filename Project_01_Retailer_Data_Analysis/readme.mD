<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Beverage Retail Sales Analysis - README</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f7fa;
        }
        .container {
            background-color: #ffffff;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        h1 {
            color: #1a2a6c;
            border-bottom: 3px solid #1a2a6c;
            padding-bottom: 10px;
            margin-top: 0;
        }
        h2 {
            color: #2c3e50;
            margin-top: 30px;
            border-bottom: 2px solid #e0e0e0;
            padding-bottom: 8px;
        }
        h3 {
            color: #34495e;
            margin-top: 20px;
        }
        h4 {
            color: #455a64;
            margin-top: 15px;
        }
        .badge {
            display: inline-block;
            background-color: #1a2a6c;
            color: #ffffff;
            padding: 2px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: bold;
            margin-right: 5px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            font-size: 14px;
        }
        th {
            background-color: #1a2a6c;
            color: #ffffff;
            padding: 12px 15px;
            text-align: left;
            font-weight: 600;
        }
        td {
            padding: 10px 15px;
            border-bottom: 1px solid #e0e0e0;
        }
        tr:nth-child(even) {
            background-color: #f8f9fa;
        }
        tr:hover {
            background-color: #e8f0fe;
        }
        .dataset-box {
            background-color: #f8f9fa;
            border-left: 4px solid #1a2a6c;
            padding: 15px 20px;
            margin: 15px 0;
            border-radius: 0 5px 5px 0;
        }
        .dataset-box strong {
            color: #1a2a6c;
        }
        .kpi-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        .kpi-card {
            background-color: #f8f9fa;
            padding: 15px 20px;
            border-radius: 8px;
            border-top: 4px solid #1a2a6c;
        }
        .kpi-card .value {
            font-size: 24px;
            font-weight: bold;
            color: #1a2a6c;
        }
        .kpi-card .label {
            font-size: 14px;
            color: #666;
            margin-top: 5px;
        }
        ul, ol {
            padding-left: 25px;
        }
        li {
            margin: 5px 0;
        }
        .highlight {
            background-color: #fff3cd;
            padding: 2px 6px;
            border-radius: 3px;
        }
        .footer {
            margin-top: 40px;
            padding-top: 20px;
            border-top: 2px solid #e0e0e0;
            text-align: center;
            color: #666;
            font-size: 14px;
        }
        .schema-table th {
            background-color: #2c3e50;
        }
        .findings-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin: 15px 0;
        }
        .findings-card {
            background-color: #f8f9fa;
            padding: 15px 20px;
            border-radius: 8px;
        }
        .findings-card .title {
            font-weight: bold;
            color: #1a2a6c;
            font-size: 16px;
        }
        @media (max-width: 768px) {
            .container {
                padding: 20px;
            }
            .findings-grid {
                grid-template-columns: 1fr;
            }
            .kpi-grid {
                grid-template-columns: 1fr 1fr;
            }
        }
        @media (max-width: 480px) {
            .kpi-grid {
                grid-template-columns: 1fr;
            }
        }
        .code-block {
            background-color: #2d2d2d;
            color: #f8f8f2;
            padding: 15px;
            border-radius: 5px;
            font-family: 'Courier New', monospace;
            font-size: 13px;
            overflow-x: auto;
            margin: 10px 0;
        }
        .version-tag {
            display: inline-block;
            background-color: #e74c3c;
            color: #fff;
            padding: 2px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: bold;
        }
    </style>
</head>
<body>

<div class="container">

    <!-- Header -->
    <div style="display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap;">
        <h1>📊 Beverage Retail Sales Analysis</h1>
        <span class="version-tag">v1.0</span>
    </div>
    <p style="color: #666; font-size: 16px; margin-top: -10px;">
        <strong>Comprehensive Sales Performance Analysis · January 2022 – December 2022</strong>
    </p>

    <!-- Project Overview -->
    <h2>📋 Project Overview</h2>
    <p>
        This project presents a comprehensive sales performance analysis of beverage products across four major retail chains: 
        <strong>Costco</strong>, <strong>Target</strong>, <strong>Walgreens</strong>, and <strong>Walmart</strong>. 
        The analysis encompasses sales data from <strong>January 2022</strong> through <strong>December 2022</strong>, 
        providing insights into revenue patterns, product performance, regional market dynamics, and operational metrics.
    </p>

    <!-- Dataset Description -->
    <h2>📁 Dataset Description</h2>
    <p>
        The analysis utilizes four primary datasets, each representing sales transactions from a specific retailer:
    </p>

    <div class="dataset-box">
        <h3 style="margin-top: 0; color: #1a2a6c;">1. Retailer_Costco.xlsx</h3>
        <table style="width: auto; margin: 5px 0;">
            <tr><td><strong>Retailer</strong></td><td>Costco</td></tr>
            <tr><td><strong>Region</strong></td><td>West – California</td></tr>
            <tr><td><strong>Contact</strong></td><td>Ana - Costco</td></tr>
            <tr><td><strong>Retailer ID</strong></td><td>1128299</td></tr>
            <tr><td><strong>Records</strong></td><td>72 transaction entries</td></tr>
            <tr><td><strong>Product Categories</strong></td><td>Coca-Cola, Diet Coke, Sprite, Fanta, Powerade, Dasani Water</td></tr>
        </table>
    </div>

    <div class="dataset-box">
        <h3 style="margin-top: 0; color: #1a2a6c;">2. Retailer_Target.xlsx</h3>
        <table style="width: auto; margin: 5px 0;">
            <tr><td><strong>Retailer</strong></td><td>Target</td></tr>
            <tr><td><strong>Region</strong></td><td>South – Texas</td></tr>
            <tr><td><strong>Contact</strong></td><td>Stuart - Target</td></tr>
            <tr><td><strong>Retailer ID</strong></td><td>1197831</td></tr>
            <tr><td><strong>Records</strong></td><td>72 transaction entries</td></tr>
            <tr><td><strong>Product Categories</strong></td><td>Coca-Cola, Diet Coke, Sprite, Fanta, Powerade, Dasani Water</td></tr>
        </table>
    </div>

    <div class="dataset-box">
        <h3 style="margin-top: 0; color: #1a2a6c;">3. Retailer_Walgreens.xlsx</h3>
        <table style="width: auto; margin: 5px 0;">
            <tr><td><strong>Retailer</strong></td><td>Walgreens</td></tr>
            <tr><td><strong>Region</strong></td><td>West – California</td></tr>
            <tr><td><strong>Contact</strong></td><td>Maria - Walgreens</td></tr>
            <tr><td><strong>Retailer ID</strong></td><td>1189833</td></tr>
            <tr><td><strong>Records</strong></td><td>72 transaction entries</td></tr>
            <tr><td><strong>Product Categories</strong></td><td>Coca-Cola, Diet Coke, Sprite, Fanta, Powerade, Dasani Water</td></tr>
        </table>
    </div>

    <div class="dataset-box">
        <h3 style="margin-top: 0; color: #1a2a6c;">4. Retailer_Walmart.xlsx</h3>
        <table style="width: auto; margin: 5px 0;">
            <tr><td><strong>Retailer</strong></td><td>Walmart</td></tr>
            <tr><td><strong>Region</strong></td><td>Northeast – New York</td></tr>
            <tr><td><strong>Contact</strong></td><td>Allen - Walmart</td></tr>
            <tr><td><strong>Retailer ID</strong></td><td>1185732</td></tr>
            <tr><td><strong>Records</strong></td><td>72 transaction entries</td></tr>
            <tr><td><strong>Product Categories</strong></td><td>Coca-Cola, Diet Coke, Sprite, Fanta, Powerade, Dasani Water</td></tr>
        </table>
    </div>

    <!-- Data Schema -->
    <h2>📐 Data Schema</h2>
    <p>Each dataset contains the following fields:</p>

    <table class="schema-table">
        <thead>
            <tr>
                <th>Field</th>
                <th>Description</th>
                <th>Data Type</th>
            </tr>
        </thead>
        <tbody>
            <tr><td>Retailer</td><td>Retail chain name</td><td>String</td></tr>
            <tr><td>Contact</td><td>Account representative</td><td>String</td></tr>
            <tr><td>Retailer ID</td><td>Unique retailer identifier</td><td>Integer</td></tr>
            <tr><td>Order Date</td><td>Date of order placement</td><td>Date</td></tr>
            <tr><td>Payment Date</td><td>Date of payment receipt</td><td>Date</td></tr>
            <tr><td>Region--State</td><td>Geographic location</td><td>String</td></tr>
            <tr><td>Beverage Brand</td><td>Product name</td><td>String</td></tr>
            <tr><td>Price per Unit</td><td>Unit price in USD</td><td>Float</td></tr>
            <tr><td>Units Sold</td><td>Quantity purchased</td><td>Integer</td></tr>
            <tr><td>Revenue</td><td>Total revenue (calculated)</td><td>Float</td></tr>
        </tbody>
    </table>

    <!-- KPI Analysis -->
    <h2>🎯 Key Performance Indicators (KPIs) Analysis</h2>

    <h3>1. Sales Performance & Volume</h3>
    <ul>
        <li><strong>Total Revenue by Retailer</strong> – Assessment of revenue contribution across retail partners</li>
        <li><strong>Top Performing Retailer</strong> – Identification of highest revenue-generating channel</li>
        <li><strong>Best-Selling Beverage Brands</strong> – Analysis of unit sales volume by product</li>
        <li><strong>Average Price per Unit</strong> – Comparative pricing analysis across brands</li>
    </ul>

    <h3>2. Temporal Trends</h3>
    <ul>
        <li><strong>Monthly Sales Growth</strong> – Tracking sales volume progression throughout 2022</li>
        <li><strong>Seasonal Patterns</strong> – Identification of peak sales periods and demand fluctuations</li>
    </ul>

    <h3>3. Geographic & Regional Insights</h3>
    <ul>
        <li><strong>Regional Market Share</strong> – Analysis of sales distribution across Northeast, South, and West regions</li>
        <li><strong>Brand Popularity by State</strong> – Product preference patterns by geographic location</li>
    </ul>

    <h3>4. Operational & Data Integrity</h3>
    <ul>
        <li><strong>Data Source Audit</strong> – Verification of data completeness (288 total records)</li>
        <li><strong>Contact/Account Coverage</strong> – Assessment of account coverage consistency</li>
        <li><strong>Price Variation Analysis</strong> – Examination of price range and variance by brand</li>
    </ul>

    <h3>5. Retailer Comparison</h3>
    <ul>
        <li><strong>Retailer × Beverage Brand Matrix</strong> – Cross-tabulation of sales volume by retailer and product</li>
    </ul>

    <h3>6. Advanced Business Insights</h3>
    <ul>
        <li><strong>Revenue Concentration</strong> – Analysis of revenue distribution across product categories</li>
    </ul>

    <!-- Dashboard -->
    <h2>📊 Interactive Dashboard</h2>
    <p>
        The project includes a comprehensive <strong>KPI Dashboard</strong> (accessible via the <code>KPI.xlsx</code> file) featuring:
    </p>
    <ul>
        <li><strong>Total Revenue by Retailer</strong> – Visual comparison of retailer performance</li>
        <li><strong>Top Retailer Identification</strong> – Clear indicator of market leader</li>
        <li><strong>Beverage Brand Performance</strong> – Units sold and revenue metrics</li>
        <li><strong>Price Analysis Dashboard</strong> – Min, max, and average price tracking</li>
        <li><strong>Regional Analysis</strong> – Geographic performance breakdown</li>
        <li><strong>Monthly Trends</strong> – Time-series visualization of sales patterns</li>
    </ul>

    <!-- Key Findings -->
    <h2>🔑 Key Findings</h2>

    <div class="findings-grid">
        <div class="findings-card">
            <div class="title">💰 Revenue Performance</div>
            <ul style="margin: 8px 0 0 0; padding-left: 20px;">
                <li><strong>Total Revenue:</strong> $1,213,017.50</li>
                <li><strong>Top Performer:</strong> Walmart ($391,767.50)</li>
                <li><strong>Second:</strong> Costco ($331,750)</li>
                <li><strong>Third:</strong> Walgreens ($250,650)</li>
                <li><strong>Fourth:</strong> Target ($238,850)</li>
            </ul>
        </div>

        <div class="findings-card">
            <div class="title">🥤 Product Performance</div>
            <ul style="margin: 8px 0 0 0; padding-left: 20px;">
                <li><strong>Best-Selling:</strong> Coca-Cola (461,900 units)</li>
                <li><strong>Second:</strong> Diet Coke (413,750 units)</li>
                <li><strong>Third:</strong> Dasani Water (392,750 units)</li>
                <li><strong>Highest Revenue:</strong> Dasani Water ($233,775)</li>
                <li><strong>Highest Unit Price:</strong> Dasani Water ($0.80 max)</li>
            </ul>
        </div>

        <div class="findings-card">
            <div class="title">📍 Regional Insights</div>
            <ul style="margin: 8px 0 0 0; padding-left: 20px;">
                <li><strong>West Region:</strong> 1,037,250 units (44.9%)</li>
                <li><strong>Northeast Region:</strong> 706,600 units (30.6%)</li>
                <li><strong>South Region:</strong> 566,000 units (24.5%)</li>
                <li><strong>Total Units Sold:</strong> 2,309,850</li>
            </ul>
        </div>

        <div class="findings-card">
            <div class="title">💰 Price Analysis</div>
            <ul style="margin: 8px 0 0 0; padding-left: 20px;">
                <li><strong>Price Range:</strong> $0.25 – $0.80</li>
                <li><strong>Highest Avg Price:</strong> Dasani Water ($0.59)</li>
                <li><strong>Lowest Avg Price:</strong> Coca-Cola ($0.48)</li>
            </ul>
        </div>
    </div>

    <!-- Technical Implementation -->
    <h2>⚙️ Technical Implementation</h2>
    <ul>
        <li><strong>Platform:</strong> Microsoft Excel</li>
        <li><strong>Data Processing:</strong> Pivot tables, formulas, and data validation</li>
        <li><strong>Dashboard Tools:</strong> GETPIVOTDATA functions for dynamic data retrieval</li>
        <li><strong>Data Volume:</strong> 288 transaction records across 4 retailers, 6 products, and 12 months</li>
    </ul>

    <!-- Usage Instructions -->
    <h2>📖 Usage Instructions</h2>
    <ol>
        <li>Open <code>KPI.xlsx</code> to access the interactive dashboard</li>
        <li>Navigate to the <code>KPI_Analysis</code> sheet for detailed metrics</li>
        <li>Review the <code>Dashboard</code> sheet for visual representations</li>
        <li>Reference individual retailer files for granular transaction data</li>
    </ol>

    <!-- Summary Statistics -->
    <h2>📈 Summary Statistics</h2>

    <div class="kpi-grid">
        <div class="kpi-card">
            <div class="value">$1.21M</div>
            <div class="label">Total Revenue</div>
        </div>
        <div class="kpi-card">
            <div class="value">2.31M</div>
            <div class="label">Total Units Sold</div>
        </div>
        <div class="kpi-card">
            <div class="value">288</div>
            <div class="label">Total Records</div>
        </div>
        <div class="kpi-card">
            <div class="value">4</div>
            <div class="label">Retailers</div>
        </div>
        <div class="kpi-card">
            <div class="value">6</div>
            <div class="label">Products</div>
        </div>
        <div class="kpi-card">
            <div class="value">12</div>
            <div class="label">Months</div>
        </div>
    </div>

    <!-- Footer -->
    <div class="footer">
        <p>
            <strong>Beverage Retail Sales Analysis Project</strong><br>
            Developed as part of a comprehensive sales performance analysis initiative<br>
            to support strategic decision-making for beverage retail distribution across multiple channels.
        </p>
        <p style="margin-top: 10px; font-size: 12px; color: #999;">
            © 2026 · All Rights Reserved
        </p>
    </div>

</div>

</body>
</html>
