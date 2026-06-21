<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Accessories Sales Dashboard</title>
    <!-- Chart.js CDN -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js">
    </script>
    <style>
        /* ─── Reset & Base ─── */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Roboto, system-ui, -apple-system, sans-serif;
            background: #f4f7fc;
            padding: 24px;
            color: #1e293b;
        }

        .dashboard {
            max-width: 1440px;
            margin: 0 auto;
        }

        /* ─── Header ─── */
        .header {
            margin-bottom: 32px;
        }
        .header h1 {
            font-weight: 600;
            font-size: 2rem;
            letter-spacing: -0.5px;
            color: #0b2b4a;
        }
        .header p {
            color: #475569;
            font-size: 1rem;
            margin-top: 4px;
        }

        /* ─── KPI Cards ─── */
        .kpi-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 20px;
            margin-bottom: 32px;
        }
        .kpi-card {
            background: #ffffff;
            border-radius: 20px;
            padding: 20px 20px 18px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.04);
            border: 1px solid #e9eef3;
            transition: 0.2s;
        }
        .kpi-card:hover {
            border-color: #b9c7d9;
        }
        .kpi-label {
            font-size: 0.85rem;
            font-weight: 500;
            text-transform: uppercase;
            letter-spacing: 0.3px;
            color: #64748b;
            margin-bottom: 6px;
        }
        .kpi-value {
            font-size: 2rem;
            font-weight: 700;
            color: #0b2b4a;
            line-height: 1.2;
        }
        .kpi-sub {
            font-size: 0.85rem;
            color: #475569;
            margin-top: 4px;
        }

        /* ─── Charts ─── */
        .chart-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
            margin-bottom: 32px;
        }
        .chart-box {
            background: #ffffff;
            border-radius: 20px;
            padding: 20px 20px 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.04);
            border: 1px solid #e9eef3;
        }
        .chart-box h3 {
            font-weight: 500;
            font-size: 1.1rem;
            margin-bottom: 16px;
            color: #1e293b;
        }
        .chart-box canvas {
            width: 100% !important;
            height: auto !important;
            max-height: 260px;
        }

        .full-width {
            grid-column: 1 / -1;
        }

        /* ─── Tables ─── */
        .table-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
            margin-bottom: 32px;
        }
        .table-box {
            background: #ffffff;
            border-radius: 20px;
            padding: 20px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.04);
            border: 1px solid #e9eef3;
        }
        .table-box h3 {
            font-weight: 500;
            font-size: 1.1rem;
            margin-bottom: 14px;
            color: #1e293b;
        }
        .table-box table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.95rem;
        }
        .table-box th {
            text-align: left;
            padding: 8px 0 8px 0;
            font-weight: 600;
            color: #475569;
            border-bottom: 2px solid #e2e8f0;
        }
        .table-box td {
            padding: 8px 0;
            border-bottom: 1px solid #f1f5f9;
        }
        .table-box tr:last-child td {
            border-bottom: none;
        }
        .table-box .total-row td {
            font-weight: 600;
            color: #0b2b4a;
        }

        /* ─── Responsive ─── */
        @media (max-width: 800px) {
            .chart-row {
                grid-template-columns: 1fr;
            }
            .table-grid {
                grid-template-columns: 1fr;
            }
            .kpi-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            body {
                padding: 16px;
            }
        }
        @media (max-width: 480px) {
            .kpi-grid {
                grid-template-columns: 1fr 1fr;
            }
            .kpi-value {
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="dashboard">

        <!-- ═══ HEADER ═══ -->
        <div class="header">
            <h1>📦 Accessories Sales Dashboard</h1>
            <p>September 2025 – January 2027 &nbsp;·&nbsp; 500+ transactions &nbsp;·&nbsp; 7 product categories</p>
        </div>

        <!-- ═══ KPI CARDS (injected by JS) ═══ -->
        <div class="kpi-grid" id="kpiContainer"></div>

        <!-- ═══ CHARTS: Region & Product ═══ -->
        <div class="chart-row">
            <div class="chart-box">
                <h3>💰 Revenue by Region</h3>
                <canvas id="regionChart"></canvas>
            </div>
            <div class="chart-box">
                <h3>📦 Revenue by Product</h3>
                <canvas id="productChart"></canvas>
            </div>
        </div>

        <!-- ═══ Monthly Trend (full width) ═══ -->
        <div class="chart-row">
            <div class="chart-box full-width">
                <h3>📈 Monthly Sales Trend</h3>
                <canvas id="monthlyChart"></canvas>
            </div>
        </div>

        <!-- ═══ TABLES: Quantity & Region ═══ -->
        <div class="table-grid">
            <div class="table-box">
                <h3>📋 Quantity by Product</h3>
                <table id="qtyTable">
                    <thead><tr><th>Product</th><th style="text-align:right;">Qty</th></tr></thead>
                    <tbody id="qtyTableBody"></tbody>
                </table>
            </div>
            <div class="table-box">
                <h3>📍 Region Sales Summary</h3>
                <table id="regionTable">
                    <thead><tr><th>Region</th><th style="text-align:right;">Revenue ($)</th></tr></thead>
                    <tbody id="regionTableBody"></tbody>
                </table>
            </div>
        </div>

        <!-- ═══ Footer ═══ -->
        <div style="text-align:center; margin-top:20px; color:#94a3b8; font-size:0.85rem;">
            Data sourced from <code>Accessories_sales_analysis.xlsx</code> &nbsp;·&nbsp; Dashboard built with Chart.js
        </div>
    </div>

    <script>
        // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
        //  1.  DATA  (from the Excel kpi sheet)
        // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

        // Revenue by Region
        const regionData = {
            labels: ['East', 'North', 'South', 'West'],
            values: [779410, 666900, 1243690, 1174540]
        };

        // Revenue by Product
        const productData = {
            labels: ['Backpack', 'Chair', 'Charger', 'Desk Lamp', 'Notebook', 'Pen Set', 'USB Drive'],
            values: [666090, 484900, 538040, 483070, 504280, 644100, 544060]
        };

        // Monthly Sales (Jan–Dec)
        const monthLabels = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
        const monthlyValues = [
            425430, 125240, 253560, 201500, 276490, 115230,
            441040, 412830, 411990, 469260, 300490, 431480
        ];

        // Quantity by Product
        const qtyData = {
            labels: ['Backpack', 'Chair', 'Charger', 'Desk Lamp', 'Notebook', 'Pen Set', 'USB Drive'],
            values: [354, 369, 446, 381, 383, 424, 446]
        };

        // Totals (from kpi GETPIVOTDATA)
        const totalRevenue = 3864540;
        const totalQuantity = 2803;

        // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
        //  2.  RENDER KPI CARDS
        // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

        const kpiContainer = document.getElementById('kpiContainer');

        // Determine top region & top product
        const topRegionIdx = regionData.values.indexOf(Math.max(...regionData.values));
        const topRegion = regionData.labels[topRegionIdx];
        const topRegionVal = regionData.values[topRegionIdx];

        const topProductIdx = productData.values.indexOf(Math.max(...productData.values));
        const topProduct = productData.labels[topProductIdx];
        const topProductVal = productData.values[topProductIdx];

        const kpis = [
            { label: 'Total Revenue', value: '$' + totalRevenue.toLocaleString(), sub: '' },
            { label: 'Total Quantity', value: totalQuantity.toLocaleString(), sub: 'units sold' },
            { label: 'Top Region', value: topRegion, sub: '$' + topRegionVal.toLocaleString() },
            { label: 'Top Product', value: topProduct, sub: '$' + topProductVal.toLocaleString() }
        ];

        kpis.forEach(k => {
            const card = document.createElement('div');
            card.className = 'kpi-card';
            card.innerHTML = `
                <div class="kpi-label">${k.label}</div>
                <div class="kpi-value">${k.value}</div>
                ${k.sub ? `<div class="kpi-sub">${k.sub}</div>` : ''}
            `;
            kpiContainer.appendChild(card);
        });

        // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
        //  3.  CHARTS  (Chart.js)
        // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

        const commonOptions = {
            responsive: true,
            maintainAspectRatio: true,
            plugins: { legend: { display: false } },
            scales: {
                y: {
                    beginAtZero: true,
                    ticks: { callback: v => '$' + v.toLocaleString() }
                }
            }
        };

        // ── Region Chart ──
        new Chart(document.getElementById('regionChart'), {
            type: 'bar',
            data: {
                labels: regionData.labels,
                datasets: [{
                    label: 'Revenue',
                    data: regionData.values,
                    backgroundColor: ['#3b82f6', '#8b5cf6', '#06b6d4', '#f59e0b'],
                    borderRadius: 6
                }]
            },
            options: commonOptions
        });

        // ── Product Chart ──
        new Chart(document.getElementById('productChart'), {
            type: 'bar',
            data: {
                labels: productData.labels,
                datasets: [{
                    label: 'Revenue',
                    data: productData.values,
                    backgroundColor: '#10b981',
                    borderRadius: 6
                }]
            },
            options: commonOptions
        });

        // ── Monthly Trend (line) ──
        new Chart(document.getElementById('monthlyChart'), {
            type: 'line',
            data: {
                labels: monthLabels,
                datasets: [{
                    label: 'Revenue',
                    data: monthlyValues,
                    borderColor: '#6366f1',
                    backgroundColor: 'rgba(99,102,241,0.1)',
                    fill: true,
                    tension: 0.3,
                    pointBackgroundColor: '#6366f1',
                    pointRadius: 4
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: true,
                plugins: { legend: { display: false } },
                scales: {
                    y: {
                        beginAtZero: true,
                        ticks: { callback: v => '$' + v.toLocaleString() }
                    }
                }
            }
        });

        // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
        //  4.  TABLES
        // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

        // ── Quantity Table ──
        const qtyBody = document.getElementById('qtyTableBody');
        let qtySum = 0;
        qtyData.labels.forEach((label, i) => {
            const val = qtyData.values[i];
            qtySum += val;
            const row = document.createElement('tr');
            row.innerHTML = `<td>${label}</td><td style="text-align:right;">${val}</td>`;
            qtyBody.appendChild(row);
        });
        const totalQtyRow = document.createElement('tr');
        totalQtyRow.className = 'total-row';
        totalQtyRow.innerHTML =
            `<td><strong>Total</strong></td><td style="text-align:right;"><strong>${qtySum}</strong></td>`;
        qtyBody.appendChild(totalQtyRow);

        // ── Region Table ──
        const regionBody = document.getElementById('regionTableBody');
        let regionSum = 0;
        regionData.labels.forEach((label, i) => {
            const val = regionData.values[i];
            regionSum += val;
            const row = document.createElement('tr');
            row.innerHTML = `<td>${label}</td><td style="text-align:right;">$${val.toLocaleString()}</td>`;
            regionBody.appendChild(row);
        });
        const totalRegionRow = document.createElement('tr');
        totalRegionRow.className = 'total-row';
        totalRegionRow.innerHTML =
            `<td><strong>Grand Total</strong></td><td style="text-align:right;"><strong>$${regionSum.toLocaleString()}</strong></td>`;
        regionBody.appendChild(totalRegionRow);
    </script>
</body>
</html>
