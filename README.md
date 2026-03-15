<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> THE COLLECTIVE SOCIETY</title>
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --success: #2ecc71;
            --danger: #e74c3c;
            --warning: #f39c12;
            --info: #1abc9c;
            --light: #ecf0f1;
            --dark: #34495e;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background: var(--primary);
            color: white;
            padding: 20px;
            border-radius: 8px 8px 0 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .status {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .status-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background-color: #e74c3c;
        }
        
        .status-dot.connected {
            background-color: #2ecc71;
        }
        
        .token-section {
            display: flex;
            gap: 10px;
            align-items: center;
            background: rgba(255,255,255,0.1);
            padding: 5px 10px;
            border-radius: 20px;
        }
        
        .token-section input {
            padding: 5px 10px;
            border: none;
            border-radius: 15px;
            width: 200px;
        }
        
        .token-section button {
            background: var(--secondary);
            border: none;
            color: white;
            padding: 5px 10px;
            border-radius: 15px;
            cursor: pointer;
            font-size: 12px;
        }
        
        .token-section button.clear {
            background: var(--danger);
        }
        
        .dashboard {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-top: 20px;
        }
        
        .panel {
            background: white;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            padding: 20px;
        }
        
        .panel-header {
            border-bottom: 1px solid #eee;
            padding-bottom: 15px;
            margin-bottom: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .panel-title {
            font-size: 18px;
            font-weight: 600;
            color: var(--primary);
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        select, input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 14px;
        }
        
        .btn {
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s;
        }
        
        .btn-primary { background: var(--secondary); color: white; }
        .btn-success { background: var(--success); color: white; }
        .btn-danger { background: var(--danger); color: white; }
        .btn-warning { background: var(--warning); color: white; }
        .btn-info { background: var(--info); color: white; }
        .btn-secondary { background: #95a5a6; color: white; }
        
        .btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }
        
        .btn-group {
            display: flex;
            gap: 10px;
            margin-top: 15px;
            flex-wrap: wrap;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .stat-card {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 6px;
            text-align: center;
        }
        
        .stat-value {
            font-size: 20px;
            font-weight: 600;
            color: var(--primary);
        }
        
        .stat-label {
            font-size: 14px;
            color: #6c757d;
        }
        
        .quote-display {
            display: flex;
            gap: 10px;
            margin: 15px 0;
        }
        
        .quote-box {
            width: 60px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: #f8f9fa;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-weight: 600;
        }
        
        .quote-trigger {
            background: var(--warning);
            color: white;
        }
        
        .log-container {
            height: 300px;
            overflow-y: auto;
            border: 1px solid #ddd;
            border-radius: 4px;
            padding: 10px;
            background: #1e272e;
            color: #f5f6fa;
            font-family: 'Courier New', monospace;
            font-size: 13px;
        }
        
        .log-entry {
            margin-bottom: 5px;
            padding: 3px 0;
        }
        
        .log-time { color: #a4b0be; }
        .log-info { color: #2ecc71; }
        .log-warning { color: #f39c12; }
        .log-error { color: #e74c3c; }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid #eee;
        }
        
        th {
            background: #f8f9fa;
            font-weight: 600;
        }
        
        tr.current-level {
            background: #e3f2fd;
        }
        
        @media (max-width: 768px) {
            .dashboard {
                grid-template-columns: 1fr;
            }
        }
        
        .strategy-section {
            margin-top: 20px;
            padding: 15px;
            background: #f0f8ff;
            border-radius: 8px;
            border: 1px solid #cce5ff;
        }
        
        .pattern-display {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 10px;
        }
        
        .pattern-item {
            padding: 5px 10px;
            background: #e3f2fd;
            border-radius: 4px;
            font-size: 12px;
        }
        
        .model-metrics {
            margin-top: 15px;
            padding: 10px;
            background: #e8f5e9;
            border-radius: 4px;
            font-size: 12px;
        }
        
        .metrics-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 5px;
        }
        
        .metric-item {
            display: flex;
            justify-content: space-between;
        }
        
        .hidden {
            display: none;
        }
        
        .progress-bar {
            height: 10px;
            background: #ecf0f1;
            border-radius: 5px;
            margin: 10px 0;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            background: var(--info);
            width: 0%;
            transition: width 0.3s;
        }
        
        .indicator-display {
            margin-top: 15px;
            padding: 10px;
            background: #fff8e1;
            border-radius: 4px;
            font-size: 12px;
        }
        
        .backtest-panel {
            margin-top: 20px;
            border-top: 2px solid var(--info);
            padding-top: 20px;
        }
        
        .backtest-controls {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            align-items: flex-end;
        }
        
        .backtest-results {
            margin-top: 15px;
            background: #f0f0f0;
            padding: 15px;
            border-radius: 4px;
        }
        
        .backtest-row {
            display: flex;
            gap: 20px;
        }
        
        .fake-progress {
            margin-top: 10px;
            font-weight: 500;
            color: var(--dark);
        }
        
        .master-ready-badge {
            background: var(--success);
            color: white;
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 12px;
            display: inline-block;
            margin-left: 10px;
        }
    </style>
</head>
<body>
<div class="container">
    <header>
        <h1> THE COLLECTIVE SOCIETY</h1>
        <div style="display: flex; gap: 20px; align-items: center;">
            <div class="token-section">
                <input type="password" id="tokenInput" placeholder="Enter API token" value="">
                <button id="setTokenBtn" class="btn-primary" style="padding: 5px 10px;">Set</button>
                <button id="clearTokenBtn" class="clear" style="padding: 5px 10px;">Clear</button>
            </div>
            <div class="status">
                <div class="status-dot" id="statusDot"></div>
                <span id="statusText">Disconnected</span>
            </div>
        </div>
    </header>

    <div class="dashboard">
        <div class="panel">
            <div class="panel-header">
                <h2 class="panel-title">Trading Controls</h2>
            </div>

            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-value" id="balanceValue">$10000.00</div>
                    <div class="stat-label">Balance</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="currentLevelValue">1</div>
                    <div class="stat-label">Martingale Level</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="currentStakeValue">$0.35</div>
                    <div class="stat-label">Current Stake</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="payoutValue">$0.31</div>
                    <div class="stat-label">Payout</div>
                </div>
            </div>

            <div class="btn-group">
                <button class="btn btn-success" id="startBotBtn">Start Bot</button>
                <button class="btn btn-danger" id="stopBotBtn" disabled>Stop Bot</button>
                <button class="btn btn-primary" id="applyStepperBtn"><b><i>Apply Stepper Strategy</i></b></button>
                <button class="btn btn-info" id="applyMasterBtn"><b><i>Apply Master Strategy</i></b></button>
            </div>

            <div class="form-group">
                <label for="market">Market</label>
                <select id="market">
                    <option value="R_10">Volatility 10 Index</option>
                    <option value="R_25">Volatility 25 Index</option>
                    <option value="R_100">Volatility 100 Index</option>
                </select>
            </div>

            <div class="form-group">
                <label for="contractType">Contract Type</label>
                <select id="contractType">
                    <option value="CALL">Rise</option>
                    <option value="PUT">Fall</option>
                    <option value="DIGITODD">Odd</option>
                    <option value="DIGITEVEN">Even</option>
                    <option value="DIGITDIFF">Differs</option>
                </select>
            </div>

            <div class="form-group" id="differsSettings" style="display:none;">
                <label>Differs Settings</label>
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-value" id="lastDiffersBarrier">-</div>
                        <div class="stat-label">Last Differs Barrier</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">Middle-digit</div>
                        <div class="stat-label">Selection mode</div>
                    </div>
                </div>
            </div>

            <div class="form-group">
                <label for="duration">Duration (ticks)</label>
                <input type="number" id="duration" value="1" min="1">
            </div>

            <div class="form-group">
                <label for="takeProfit">Take Profit ($)</label>
                <input type="number" id="takeProfit" value="10" min="0" step="0.01">
            </div>

            <div class="form-group">
                <label for="stopLoss">Stop Loss ($)</label>
                <input type="number" id="stopLoss" value="30" min="0" step="0.01">
            </div>

            <!-- Performance optimization: prediction frequency -->
            <div class="form-group">
                <label for="predictionFrequency">Prediction Frequency</label>
                <select id="predictionFrequency">
                    <option value="1">Every tick</option>
                    <option value="2">Every 2 ticks</option>
                    <option value="5">Every 5 ticks</option>
                    <option value="10">Every 10 ticks</option>
                </select>
                <small style="color: #666;">Reduce to improve performance</small>
            </div>

            <div class="btn-group">
                <button class="btn btn-primary" id="updateContractBtn">Update Parameters</button>
                <button class="btn btn-warning" id="testContractBtn">Test Contract</button>
            </div>
        </div>

        <div class="panel">
            <div class="panel-header">
                <h2 class="panel-title" id="marketTitle">Volatility 10 Index</h2>
            </div>

            <div class="form-group">
                <label>Current Price</label>
                <div class="stat-value" id="currentPriceDisplay">-</div>
            </div>

            <div class="form-group">
                <label>Recent Quotes</label>
                <div class="quote-display" id="quoteContainer">
                    <div class="quote-box">-</div>
                    <div class="quote-box">-</div>
                    <div class="quote-box">-</div>
                    <div class="quote-box">-</div>
                </div>
            </div>

            <div class="form-group">
                <label>Trade Parameters</label>
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-value" id="takeProfitValue">$10.00</div>
                        <div class="stat-label">Take Profit</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" id="stopLossValue">$30.00</div>
                        <div class="stat-label">Stop Loss</div>
                    </div>
                </div>
            </div>

            <div class="panel-header">
                <h2 class="panel-title">Martingale Levels</h2>
            </div>

            <div style="overflow-x: auto;">
                <table>
                    <thead>
                    <tr>
                        <th>Level</th>
                        <th>Stake</th>
                        <th>Payout</th>
                    </tr>
                    </thead>
                    <tbody id="martingaleLevels">
                    <!-- Will be populated by JavaScript -->
                    </tbody>
                </table>
            </div>
            
            <div class="strategy-section">
                <h3>Pattern Recognition 
                    <span id="masterReadyBadge" class="master-ready-badge hidden">Ready</span>
                </h3>
                <div class="fake-progress" id="fakeProgress">Fake trades: 0/20 (Master strategy learning)</div>
                <div class="pattern-display" id="patternDisplay">
                    <!-- Patterns will be displayed here -->
                </div>
                
                <div class="model-metrics">
                    <h4>Model Performance Metrics</h4>
                    <div class="metrics-grid" id="metricsGrid">
                        <!-- Metrics will be displayed here -->
                    </div>
                </div>
                
                <div class="model-training hidden" id="trainingSection">
                    <h4>Model Training Progress</h4>
                    <div class="progress-bar">
                        <div class="progress-fill" id="trainingProgress"></div>
                    </div>
                    <div id="trainingStatus">Waiting to start...</div>
                </div>
                
                <div class="indicator-display">
                    <h4>Technical Indicators</h4>
                    <div id="indicatorsList">
                        <!-- Indicators will be displayed here -->
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Backtesting Panel -->
    <div class="panel backtest-panel">
        <div class="panel-header">
            <h2 class="panel-title">Backtesting Framework</h2>
            <button class="btn btn-info" id="toggleBacktestBtn">Show/Hide Backtest</button>
        </div>
        <div id="backtestSection" style="display: none;">
            <div class="backtest-controls">
                <div class="form-group" style="flex:1;">
                    <label>Market for Backtest</label>
                    <select id="backtestMarket">
                        <option value="R_10">Volatility 10 Index</option>
                        <option value="R_25">Volatility 25 Index</option>
                        <option value="R_100">Volatility 100 Index</option>
                    </select>
                </div>
                <div class="form-group" style="flex:1;">
                    <label>Number of Ticks</label>
                    <input type="number" id="backtestTicks" value="1000" min="100" step="100">
                </div>
                <div class="form-group" style="flex:1;">
                    <label>Strategy</label>
                    <select id="backtestStrategy">
                        <option value="stepper">Stepper (LWW pattern)</option>
                        <option value="master">Master Strategy (needs pre-learned)</option>
                    </select>
                </div>
                <button class="btn btn-success" id="runBacktestBtn">Run Backtest</button>
                <button class="btn btn-secondary" id="exportBacktestBtn">Export Results</button>
            </div>
            <div class="backtest-results" id="backtestResults">
                <div class="backtest-row">
                    <div><strong>Total trades:</strong> <span id="btTrades">0</span></div>
                    <div><strong>Wins:</strong> <span id="btWins">0</span></div>
                    <div><strong>Losses:</strong> <span id="btLosses">0</span></div>
                    <div><strong>Win rate:</strong> <span id="btWinRate">0%</span></div>
                    <div><strong>Net profit:</strong> <span id="btProfit">$0.00</span></div>
                </div>
                <div style="margin-top:10px; max-height:200px; overflow-y:auto;" id="backtestLog"></div>
            </div>
        </div>
    </div>

    <div class="panel" style="margin-top: 20px;">
        <div class="panel-header">
            <h2 class="panel-title">Trading Log · StepperBrain Insights</h2>
        </div>
        <div class="log-container" id="logContainer">
            <!-- Log entries will be added here -->
        </div>
    </div>
</div>

<script>
    // ==================== Enhanced StepperBrain AI with Master Strategy ====================
    class StepperBrain {
        constructor() {
            this.history = [];
            this.predictionHistory = [];
            this.failedPredictions = 0;
            this.ownLanguage = new Map();
            this.learningRate = 0.1;
            this.weights = {
                arithmetic: 1.0,
                geometric: 1.0,
                fibonacci: 1.0,
                finiteDiff: 1.0,
                pascal: 1.0,
                logistic: 1.0,
                commonDiff: 1.0
            };
            
            this.patterns = {};
            this.loops = {};
            this.patternClasses = {};
            this.fakeContracts = [];
            this.realContracts = [];
            this.triggerHistory = [];
            this.masterMode = false;
            this.patternCount = 0;
            this.dataDirectory = null;
            
            this.models = {};
            this.modelMetrics = {};
            this.trainingData = {};
            this.indicators = {};
            this.isTraining = false;
            
            this.indicatorsCache = {};
            this.masterReady = false;

            // Prediction throttling: we'll store tick counter
            this.tickCounter = 0;
            this.predictionFrequency = 1; // default
        }

        encode(num) {
            return {
                decimal: num.toString(),
                octal: '0o' + num.toString(8),
                hex: '0x' + num.toString(16),
                binary: '0b' + num.toString(2)
            };
        }

        updateOwnLanguage(num) {
            this.ownLanguage.set(num, this.encode(num));
        }

        // --- sequence predictors (original) ---
        arithmeticNext(seq) {
            if (seq.length < 2) return null;
            let d = seq[1] - seq[0];
            for (let i = 2; i < seq.length; i++) {
                if (seq[i] - seq[i-1] !== d) return null;
            }
            return seq[seq.length-1] + d;
        }

        geometricNext(seq) {
            if (seq.length < 2 || seq[0] === 0) return null;
            let r = seq[1] / seq[0];
            for (let i = 2; i < seq.length; i++) {
                if (seq[i-1] === 0 || seq[i] / seq[i-1] !== r) return null;
            }
            return seq[seq.length-1] * r;
        }

        fibonacciNext(seq) {
            if (seq.length < 2) return null;
            for (let i = 2; i < seq.length; i++) {
                if (seq[i] !== seq[i-1] + seq[i-2]) return null;
            }
            return seq[seq.length-1] + seq[seq.length-2];
        }

        finiteDifferenceNext(seq) {
            let n = seq.length;
            if (n < 3) return null;
            let diffs = [seq];
            while (true) {
                let last = diffs[diffs.length-1];
                if (last.length < 2) break;
                let diff = [];
                for (let i = 0; i < last.length-1; i++) diff.push(last[i+1] - last[i]);
                diffs.push(diff);
                if (diff.length === 0) break;
                let allEqual = diff.every(v => v === diff[0]);
                if (allEqual) {
                    let nextVal = seq[seq.length-1];
                    for (let j = diffs.length-2; j >= 1; j--) {
                        nextVal += diffs[j][diffs[j].length-1];
                    }
                    return nextVal;
                }
            }
            return null;
        }

        comb(n, k) {
            if (k < 0 || k > n) return 0;
            if (k === 0 || k === n) return 1;
            let res = 1;
            for (let i = 1; i <= k; i++) {
                res = res * (n - i + 1) / i;
            }
            return res;
        }

        pascalNext(seq) {
            let n = seq.length;
            if (n < 2) return null;
            for (let k = 1; k <= n+1; k++) {
                try {
                    if (this.comb(n, k-1) === seq[seq.length-1]) {
                        return this.comb(n+1, k);
                    }
                } catch (e) {
                    return null;
                }
            }
            return null;
        }

        logisticNext(seq, r=3.7) {
            if (seq.length < 1) return null;
            let maxVal = Math.max(...seq);
            if (maxVal === 0) maxVal = 1;
            let x = seq[seq.length-1] / maxVal;
            return Math.round(r * x * (1 - x) * maxVal);
        }

        // --- main prediction with throttling support ---
        predictNext(seq, force = false) {
            // throttling: only run full prediction if tickCounter % frequency == 0 or forced
            if (!force && this.predictionFrequency > 1) {
                // return cached last prediction? simpler: just return null to skip
                return null;
            }

            let methods = [
                { name: 'arithmetic', fn: this.arithmeticNext.bind(this) },
                { name: 'geometric', fn: this.geometricNext.bind(this) },
                { name: 'fibonacci', fn: this.fibonacciNext.bind(this) },
                { name: 'finiteDiff', fn: this.finiteDifferenceNext.bind(this) },
                { name: 'pascal', fn: this.pascalNext.bind(this) },
                { name: 'logistic', fn: this.logisticNext.bind(this) }
            ];
            let predictions = [];
            for (let m of methods) {
                try {
                    let pred = m.fn(seq);
                    if (pred !== null && !isNaN(pred) && isFinite(pred)) {
                        predictions.push({ value: pred, method: m.name, weight: this.weights[m.name] });
                    }
                } catch (e) {}
            }

            if (seq.length > 1) {
                let diffs = [];
                for (let i = 1; i < seq.length; i++) diffs.push(seq[i] - seq[i-1]);
                if (diffs.length > 0) {
                    let freq = {};
                    let maxFreq = 0, commonDiff = null;
                    for (let d of diffs) {
                        freq[d] = (freq[d] || 0) + 1;
                        if (freq[d] > maxFreq) {
                            maxFreq = freq[d];
                            commonDiff = d;
                        }
                    }
                    if (commonDiff !== null) {
                        predictions.push({ value: seq[seq.length-1] + commonDiff, method: 'commonDiff', weight: this.weights.commonDiff });
                    }
                }
            }

            if (predictions.length === 0) {
                return { value: Math.floor(Math.random() * 1001), method: 'random' };
            }

            let totalWeight = predictions.reduce((acc, p) => acc + p.weight, 0);
            if (totalWeight === 0) {
                let rand = predictions[Math.floor(Math.random() * predictions.length)];
                return { value: rand.value, method: rand.method };
            }
            let r = Math.random() * totalWeight;
            let upto = 0;
            for (let p of predictions) {
                if (upto + p.weight >= r) return { value: p.value, method: p.method };
                upto += p.weight;
            }
            return { value: predictions[predictions.length-1].value, method: predictions[predictions.length-1].method };
        }

        processInput(num) {
            this.history.push(num);
            if (this.history.length > 100) this.history.shift();

            this.updateOwnLanguage(num);

            // Throttled prediction
            this.tickCounter++;
            let shouldPredict = (this.tickCounter % this.predictionFrequency === 0);
            let predObj = shouldPredict ? this.predictNext(this.history) : null;
            
            if (predObj) {
                let pred = predObj.value;
                let method = predObj.method;
                this.predictionHistory.push({ input: num, predicted: pred, method: method });

                // adjust weights based on correctness (if we have a subsequent input to compare)
                if (this.predictionHistory.length > 1) {
                    let last = this.predictionHistory[this.predictionHistory.length-2];
                    if (last.input === pred) {
                        this.weights[last.method] = Math.min(2.0, this.weights[last.method] + this.learningRate);
                    } else {
                        this.weights[last.method] = Math.max(0.1, this.weights[last.method] - this.learningRate);
                        this.failedPredictions++;
                    }
                }

                if (this.failedPredictions > 5) {
                    this.failedPredictions = 0;
                    for (let key in this.weights) {
                        this.weights[key] = 1.0;
                    }
                }
                return pred;
            }
            return null; // no prediction this tick
        }

        getLastPrediction() {
            if (this.predictionHistory.length === 0) return null;
            return this.predictionHistory[this.predictionHistory.length-1].predicted;
        }
        
        // Enhanced pattern recognition methods
        analyzePattern(outcome, trigger, contractType, market, last5Prices) {
            const patternKey = this.patternCount++;
            const pattern = {
                id: patternKey,
                outcome: outcome,
                trigger: trigger,
                contractType: contractType,
                market: market,
                last5Prices: [...last5Prices],
                timestamp: new Date()
            };
            
            this.patterns[patternKey] = pattern;
            
            const frac = trigger - Math.floor(trigger);
            const classIndex = Math.floor(frac * 26) % 26;
            const patternClass = String.fromCharCode(97 + classIndex);
            if (!this.patternClasses[patternClass]) {
                this.patternClasses[patternClass] = [];
            }
            this.patternClasses[patternClass].push(patternKey);
            
            if (this.patternClasses[patternClass].length >= 3) {
                const loopId = `loop_${patternClass}_${this.patternClasses[patternClass].length}`;
                if (!this.loops[loopId]) {
                    this.loops[loopId] = {
                        class: patternClass,
                        patterns: this.patternClasses[patternClass].slice(-3),
                        firstSeen: new Date()
                    };
                }
            }
            
            if (this.dataDirectory) {
                this.saveToStorage();
            }
            
            return pattern;
        }
        
        detectLoop(patterns) {
            if (patterns.length < 3) return null;
            const lastThree = patterns.slice(-3);
            for (let i = 0; i < patterns.length - 3; i++) {
                if (patterns[i] === lastThree[0] && 
                    patterns[i+1] === lastThree[1] && 
                    patterns[i+2] === lastThree[2]) {
                    return { startIndex: i, endIndex: i + 2, patternSequence: lastThree };
                }
            }
            return null;
        }
        
        recordFakeContract(outcome, trigger, contractType, market, last5Prices) {
            const fakeContract = {
                outcome: outcome,
                trigger: trigger,
                contractType: contractType,
                market: market,
                last5Prices: [...last5Prices],
                timestamp: new Date()
            };
            
            this.fakeContracts.push(fakeContract);
            this.analyzePattern(outcome, trigger, contractType, market, last5Prices);
            
            // After 20 fake contracts, master mode becomes ready
            if (this.fakeContracts.length >= 20 && this.masterMode && !this.masterReady) {
                this.masterReady = true;
                addLog('Stepper server connected. Do not be greedy.', 'info');
                // Update UI badge
                const badge = document.getElementById('masterReadyBadge');
                if (badge) badge.classList.remove('hidden');
            }
            
            // Update fake progress UI
            updateFakeProgress(this.fakeContracts.length);
            
            return fakeContract;
        }
        
        recordRealContract(contractData) {
            this.realContracts.push({ ...contractData, timestamp: new Date() });
            this.analyzePattern(contractData.outcome, contractData.trigger, contractData.contractType, contractData.market, contractData.last5Prices);
        }
        
        decideTrade(trigger, contractType, market, last5Prices) {
            if (!this.masterMode || !this.masterReady) return null;
            
            const tolerance = 0.001;
            const similarPatterns = [];
            
            for (let id in this.patterns) {
                const p = this.patterns[id];
                if (p.market === market && 
                    Math.abs(p.trigger - trigger) < tolerance && 
                    p.contractType === contractType) {
                    similarPatterns.push(p);
                }
            }
            
            if (similarPatterns.length === 0) {
                addLog('No similar patterns found for this trigger, simulating', 'warning');
                return false;
            }
            
            let wins = similarPatterns.filter(p => p.outcome === 'win').length;
            let losses = similarPatterns.filter(p => p.outcome === 'loss').length;
            let total = wins + losses;
            let winRate = wins / total;
            
            return winRate > 0.6; // true = buy (win predicted)
        }
        
        enableMasterMode(directoryPath) {
            this.masterMode = true;
            this.dataDirectory = directoryPath || 'stepper_master_data';
            this.loadFromStorage();
            addLog(`Master strategy enabled. Data will be stored in: ${this.dataDirectory}`, 'info');
            updateFakeProgress(this.fakeContracts.length);
            if (this.fakeContracts.length >= 20) {
                this.masterReady = true;
                document.getElementById('masterReadyBadge').classList.remove('hidden');
            }
        }
        
        disableMasterMode() {
            this.masterMode = false;
            this.masterReady = false;
            document.getElementById('masterReadyBadge').classList.add('hidden');
            addLog('Master strategy disabled', 'warning');
        }
        
        saveToStorage() {
            try {
                const data = {
                    patterns: this.patterns,
                    loops: this.loops,
                    patternClasses: this.patternClasses,
                    fakeContracts: this.fakeContracts,
                    realContracts: this.realContracts,
                    patternCount: this.patternCount
                };
                localStorage.setItem(this.dataDirectory, JSON.stringify(data));
            } catch (e) {
                addLog('Failed to save data to localStorage', 'error');
            }
        }
        
        loadFromStorage() {
            try {
                const saved = localStorage.getItem(this.dataDirectory);
                if (saved) {
                    const data = JSON.parse(saved);
                    this.patterns = data.patterns || {};
                    this.loops = data.loops || {};
                    this.patternClasses = data.patternClasses || {};
                    this.fakeContracts = data.fakeContracts || [];
                    this.realContracts = data.realContracts || [];
                    this.patternCount = data.patternCount || 0;
                    addLog(`Loaded ${Object.keys(this.patterns).length} patterns from storage`, 'info');
                } else {
                    addLog('No existing data found, starting fresh', 'info');
                }
            } catch (e) {
                addLog('Failed to load data from localStorage', 'error');
            }
        }
        
        getPatterns() { return this.patterns; }
        getPatternClasses() { return this.patternClasses; }
        
        getMetrics() {
            const totalPatterns = Object.keys(this.patterns).length;
            const totalFake = this.fakeContracts.length;
            const totalReal = this.realContracts.length;
            const wins = this.realContracts.filter(c => c.outcome === 'win').length;
            const losses = this.realContracts.filter(c => c.outcome === 'loss').length;
            return {
                totalPatterns,
                totalFake,
                totalReal,
                wins,
                losses,
                winRate: totalReal > 0 ? (wins / totalReal * 100).toFixed(1) : 0
            };
        }

        // Set prediction frequency from UI
        setPredictionFrequency(freq) {
            this.predictionFrequency = parseInt(freq, 10);
        }
    }

    // ==================== Original Deriv Bot with Enhancements ====================
    const APP_ID = 86038;  // Deriv application ID (fixed)
    let TOKEN = '';        // Will be set by user input

    const MARKETS = ['R_10', 'R_25', 'R_100'];
    const PING_INTERVAL = 10000;
    const RECONNECT_DELAY = 1000;

    const martingaleSteps = [
        { stake: 0.35, payout: 0.31 },
        { stake: 0.50, payout: 0.46 },
        { stake: 1.00, payout: 0.94 },
        { stake: 2.00, payout: 1.91 }
    ];

    const triggerLists = {
        R_10: [0.000, 0.010, 0.020, 0.030, 0.040, 0.050, 0.060, 0.070, 0.080, 0.090, 0.101, 0.111, 0.121, 0.131, 0.141, 0.151, 0.161, 0.171, 0.181, 0.191, 0.202, 0.212, 0.222, 0.232, 0.242, 0.252, 0.262, 0.272, 0.282, 0.292, 0.303, 0.313, 0.323, 0.333, 0.343, 0.353, 0.363, 0.373, 0.383, 0.393, 0.404, 0.414, 0.424, 0.434, 0.444, 0.454, 0.464, 0.474, 0.484, 0.494, 0.505, 0.515, 0.525, 0.535, 0.545, 0.555, 0.565, 0.575, 0.585, 0.595, 0.606, 0.616, 0.626, 0.636, 0.646, 0.656, 0.666, 0.676, 0.686, 0.696, 0.707, 0.717, 0.727, 0.737, 0.747, 0.757, 0.767, 0.777, 0.787, 0.797, 0.808, 0.818, 0.828, 0.838, 0.848, 0.858, 0.868, 0.878, 0.888, 0.898, 0.909, 0.919, 0.929, 0.939, 0.949, 0.959, 0.969, 0.979, 0.989, 0.999],
        R_25: [0.000, 0.010, 0.020, 0.030, 0.040, 0.050, 0.060, 0.070, 0.080, 0.090, 0.101, 0.111, 0.121, 0.131, 0.141, 0.151, 0.161, 0.171, 0.181, 0.191, 0.202, 0.212, 0.222, 0.232, 0.242, 0.252, 0.262, 0.272, 0.282, 0.292, 0.303, 0.313, 0.323, 0.333, 0.343, 0.353, 0.363, 0.373, 0.383, 0.393, 0.404, 0.414, 0.424, 0.434, 0.444, 0.454, 0.464, 0.474, 0.484, 0.494, 0.505, 0.515, 0.525, 0.535, 0.545, 0.555, 0.565, 0.575, 0.585, 0.595, 0.606, 0.616, 0.626, 0.636, 0.646, 0.656, 0.666, 0.676, 0.686, 0.696, 0.707, 0.717, 0.727, 0.737, 0.747, 0.757, 0.767, 0.777, 0.787, 0.797, 0.808, 0.818, 0.828, 0.838, 0.848, 0.858, 0.868, 0.878, 0.888, 0.898, 0.909, 0.919, 0.929, 0.939, 0.949, 0.959, 0.969, 0.979, 0.989, 0.999],
        R_100: [0.00, 0.22, 0.242, 0.44, 0.66, 0.686, 0.88]
    };

    const marketNames = {
        'R_10': 'Volatility 10 Index',
        'R_25': 'Volatility 25 Index',
        'R_100': 'Volatility 100 Index'
    };

    // Data structures
    const quotes = { R_10: [], R_25: [], R_100: [] };
    const digits = { R_10: [], R_25: [], R_100: [] };
    const priceHistory = { R_10: [], R_25: [], R_100: [] };
    const barData = { R_10: {close: []}, R_25: {close: []}, R_100: {close: []} };

    // Trading state
    let ws = null;
    let pingTimer = null;
    let reconnectAttempts = 0;
    const MAX_RECONNECT_ATTEMPTS = 5;
    let isDerivConnected = false;
    let isStepperApplied = false;
    let isMasterApplied = false;
    let isBotRunning = false;
    let currentBalance = 10000;
    let initialBalance = 0;
    let currentMartingaleLevel = 0;
    let currentPrice = 0;
    let activeContracts = [];
    let tradeOutcomes = [];
    let currentStreak = { type: null, count: 0 };
    let subscriptionId = null;
    let pendingSimulation = null;
    let virtualOutcomes = [];
    let isNextReal = false;

    // StepperBrain instance
    const stepper = new StepperBrain();

    let currentContract = {
        market: 'R_10',
        type: 'CALL',
        duration: 1,
        takeProfit: 10,
        stopLoss: 30
    };

    let lastDiffersBarrier = null;
    let lastFivePrices = [];

    // DOM elements
    const startBotBtn = document.getElementById('startBotBtn');
    const stopBotBtn = document.getElementById('stopBotBtn');
    const updateContractBtn = document.getElementById('updateContractBtn');
    const testContractBtn = document.getElementById('testContractBtn');
    const applyStepperBtn = document.getElementById('applyStepperBtn');
    const applyMasterBtn = document.getElementById('applyMasterBtn');
    const statusText = document.getElementById('statusText');
    const statusDot = document.getElementById('statusDot');
    const logContainer = document.getElementById('logContainer');
    const balanceValue = document.getElementById('balanceValue');
    const marketTitle = document.getElementById('marketTitle');
    const quoteContainer = document.getElementById('quoteContainer');
    const currentPriceDisplay = document.getElementById('currentPriceDisplay');
    const diffSettingsEl = document.getElementById('differsSettings');
    const lastDiffersBarrierEl = document.getElementById('lastDiffersBarrier');
    const patternDisplay = document.getElementById('patternDisplay');
    const metricsGrid = document.getElementById('metricsGrid');
    const indicatorsList = document.getElementById('indicatorsList');
    const fakeProgress = document.getElementById('fakeProgress');
    const masterReadyBadge = document.getElementById('masterReadyBadge');
    const predictionFrequencySelect = document.getElementById('predictionFrequency');
    const tokenInput = document.getElementById('tokenInput');
    const setTokenBtn = document.getElementById('setTokenBtn');
    const clearTokenBtn = document.getElementById('clearTokenBtn');
    const toggleBacktestBtn = document.getElementById('toggleBacktestBtn');
    const backtestSection = document.getElementById('backtestSection');
    const runBacktestBtn = document.getElementById('runBacktestBtn');
    const exportBacktestBtn = document.getElementById('exportBacktestBtn');
    const backtestMarket = document.getElementById('backtestMarket');
    const backtestTicks = document.getElementById('backtestTicks');
    const backtestStrategy = document.getElementById('backtestStrategy');
    const btTrades = document.getElementById('btTrades');
    const btWins = document.getElementById('btWins');
    const btLosses = document.getElementById('btLosses');
    const btWinRate = document.getElementById('btWinRate');
    const btProfit = document.getElementById('btProfit');
    const backtestLog = document.getElementById('backtestLog');

    // Helper functions
    function addLog(message, type = 'info') {
        const now = new Date();
        const timeString = now.toLocaleTimeString();
        const logEntry = document.createElement('div');
        logEntry.className = `log-entry log-${type}`;
        logEntry.innerHTML = `<span class="log-time">[${timeString}]</span> ${message}`;
        logContainer.appendChild(logEntry);
        logContainer.scrollTop = logContainer.scrollHeight;
    }

    function updateFakeProgress(count) {
        if (fakeProgress) {
            fakeProgress.textContent = `Fake trades: ${count}/20 (Master strategy ${count >= 20 ? 'ready' : 'learning'})`;
        }
    }

    function updateConnectionStatus(connected) {
        isDerivConnected = connected;
        statusDot.classList.toggle('connected', isDerivConnected);
        statusText.textContent = isDerivConnected ? 'Connected' : 'Disconnected';
        if (connected) reconnectAttempts = 0;
    }

    function updateContractDisplay() {
        document.getElementById('market').value = currentContract.market;
        document.getElementById('contractType').value = currentContract.type;
        document.getElementById('duration').value = currentContract.duration;
        document.getElementById('takeProfit').value = currentContract.takeProfit;
        document.getElementById('stopLoss').value = currentContract.stopLoss;
        document.getElementById('takeProfitValue').textContent = `$${currentContract.takeProfit.toFixed(2)}`;
        document.getElementById('stopLossValue').textContent = `$${currentContract.stopLoss.toFixed(2)}`;
        marketTitle.textContent = marketNames[currentContract.market];
        updateMartingaleDisplay();
        diffSettingsEl.style.display = (currentContract.type === 'DIGITDIFF') ? 'block' : 'none';
        updateQuoteDisplay(currentContract.market);
    }

    function updateMartingaleDisplay() {
        const martingaleLevels = document.getElementById('martingaleLevels');
        martingaleLevels.innerHTML = '';
        martingaleSteps.forEach((step, index) => {
            const row = document.createElement('tr');
            if (index === currentMartingaleLevel) row.classList.add('current-level');
            row.innerHTML = `<td>${index + 1}</td><td>$${step.stake.toFixed(2)}</td><td>$${step.payout.toFixed(2)}</td>`;
            martingaleLevels.appendChild(row);
        });
        document.getElementById('currentLevelValue').textContent = currentMartingaleLevel + 1;
        document.getElementById('currentStakeValue').textContent = `$${martingaleSteps[currentMartingaleLevel].stake.toFixed(2)}`;
        document.getElementById('payoutValue').textContent = `$${martingaleSteps[currentMartingaleLevel].payout.toFixed(2)}`;
    }

    function getPipSize(market) {
        return (market === 'R_10' || market === 'R_25') ? 3 : 2;
    }

    function isTriggerQuote(symbol, quote, pip_size) {
        const triggerList = triggerLists[symbol];
        if (!triggerList) return false;
        const fractional = quote - Math.floor(quote);
        const quoteStr = fractional.toFixed(pip_size);
        return triggerList.some(trigger => trigger.toFixed(pip_size) === quoteStr);
    }

    function updateQuoteDisplay(symbol) {
        const marketQuotes = quotes[symbol] || [];
        const quoteBoxes = quoteContainer.querySelectorAll('.quote-box');
        quoteBoxes.forEach((box, index) => {
            if (index < marketQuotes.length) {
                const q = marketQuotes[index];
                box.textContent = q.quote.toFixed(q.pip_size);
                box.classList.toggle('quote-trigger', q.isTrigger);
            } else {
                box.textContent = '-';
                box.classList.remove('quote-trigger');
            }
        });
    }

    function getCurrentStreak() {
        if (tradeOutcomes.length === 0) return { type: null, count: 0 };
        const lastOutcome = tradeOutcomes[tradeOutcomes.length - 1];
        let count = 1;
        for (let i = tradeOutcomes.length - 2; i >= 0; i--) {
            if (tradeOutcomes[i] === lastOutcome) count++; else break;
        }
        return { type: lastOutcome, count: count };
    }

    function determineContractType() { return currentContract.type; }

    function purchaseContract(contractType = null) {
        if (!isDerivConnected) { addLog('Not connected', 'error'); return; }
        if (!contractType) contractType = determineContractType();
        const stake = martingaleSteps[currentMartingaleLevel].stake;
        const buyRequest = {
            buy: 1,
            price: stake,
            parameters: {
                amount: stake,
                basis: "stake",
                contract_type: contractType,
                currency: "USD",
                duration: currentContract.duration,
                duration_unit: "t",
                symbol: currentContract.market
            }
        };
        if (ws && ws.readyState === WebSocket.OPEN) {
            ws.send(JSON.stringify(buyRequest));
            addLog(`Purchasing ${contractType} contract on ${currentContract.market} with stake $${stake.toFixed(2)}`);
        } else addLog('WebSocket not open', 'error');
    }

    function purchaseDigitDiff(barrier) {
        if (!isDerivConnected) { addLog('Not connected', 'error'); return; }
        const stake = martingaleSteps[currentMartingaleLevel].stake;
        const buyRequest = {
            buy: 1,
            price: stake,
            parameters: {
                amount: stake,
                basis: "stake",
                contract_type: 'DIGITDIFF',
                barrier: String(barrier),
                currency: "USD",
                duration: currentContract.duration,
                duration_unit: "t",
                symbol: currentContract.market
            }
        };
        if (ws && ws.readyState === WebSocket.OPEN) {
            ws.send(JSON.stringify(buyRequest));
            addLog(`Purchasing DIGITDIFF with barrier ${barrier}`);
        }
    }

    function purchaseRiseFall(direction) {
        if (!isDerivConnected) { addLog('Not connected', 'error'); return; }
        const stake = martingaleSteps[currentMartingaleLevel].stake;
        const buyRequest = {
            buy: 1,
            price: stake,
            parameters: {
                amount: stake,
                basis: "stake",
                contract_type: direction,
                currency: "USD",
                duration: currentContract.duration,
                duration_unit: "t",
                symbol: currentContract.market
            }
        };
        if (ws && ws.readyState === WebSocket.OPEN) {
            ws.send(JSON.stringify(buyRequest));
            addLog(`Purchasing ${direction} (Rise/Fall) contract on ${currentContract.market} with stake $${stake.toFixed(2)}`);
        } else addLog('WebSocket not open', 'error');
    }

    function processTradeOutcome(contract, isWin) {
        if (isWin) {
            addLog(`Contract WON: +$${contract.payout.toFixed(2)} (level ${contract.level + 1})`, 'info');
            tradeOutcomes.push('win');
            currentMartingaleLevel = 0;
        } else {
            addLog(`Contract LOST: -$${contract.stake.toFixed(2)} (level ${contract.level + 1})`, 'warning');
            tradeOutcomes.push('loss');
            if (currentMartingaleLevel < martingaleSteps.length - 1) currentMartingaleLevel++;
        }
        updateMartingaleDisplay();
        currentStreak = getCurrentStreak();
        const netProfit = currentBalance - initialBalance;
        if (isBotRunning) {
            if (netProfit >= currentContract.takeProfit) { addLog('Take profit reached, stopping bot', 'info'); stopBot(); }
            else if (netProfit <= -currentContract.stopLoss) { addLog('Stop loss reached, stopping bot', 'warning'); stopBot(); }
        }
        addLog('Ready for next trade', 'info');
    }

    // WebSocket with error handling and reconnection
    function connectWebSocket() {
        if (!TOKEN) {
            addLog('API token not set. Please enter your token.', 'error');
            return;
        }
        if (ws && ws.readyState === WebSocket.OPEN) ws.close();
        ws = new WebSocket(`wss://ws.derivws.com/websockets/v3?app_id=${APP_ID}`);
        
        ws.onopen = () => {
            addLog('WebSocket connected');
            ws.send(JSON.stringify({ authorize: TOKEN }));
            pingTimer = setInterval(() => ws.send(JSON.stringify({ ping: 1 })), PING_INTERVAL);
            reconnectAttempts = 0;
        };
        
        ws.onmessage = (msg) => {
            try {
                const data = JSON.parse(msg.data);
                if (data.error) { 
                    addLog(`API Error: ${data.error.message}`, 'error');
                    if (data.error.code === 'InvalidToken') {
                        addLog('Invalid token. Please re-enter.', 'error');
                        updateConnectionStatus(false);
                    }
                    return; 
                }
                if (data.msg_type === 'authorize') {
                    updateConnectionStatus(true);
                    addLog('Authorized successfully');
                    initialBalance = data.authorize.balance;
                    currentBalance = initialBalance;
                    balanceValue.textContent = `$${currentBalance.toFixed(2)}`;
                    ws.send(JSON.stringify({ balance: 1, subscribe: 1 }));
                    ws.send(JSON.stringify({ proposal_open_contract: 1, subscribe: 1 }));
                    subscribeToTicks();
                } else if (data.msg_type === 'balance') {
                    currentBalance = data.balance.balance;
                    balanceValue.textContent = `$${currentBalance.toFixed(2)}`;
                } else if (data.msg_type === 'tick') {
                    processTickData(data.tick);
                } else if (data.msg_type === 'buy') {
                    const contractInfo = {
                        id: data.buy.contract_id,
                        level: currentMartingaleLevel,
                        stake: martingaleSteps[currentMartingaleLevel].stake,
                        payout: martingaleSteps[currentMartingaleLevel].payout
                    };
                    activeContracts.push(contractInfo);
                    addLog(`Contract purchased: ID ${data.buy.contract_id} at level ${currentMartingaleLevel + 1}`);
                } else if (data.msg_type === 'proposal_open_contract') {
                    if (data.proposal_open_contract && activeContracts.some(c => c.id === data.proposal_open_contract.contract_id)) {
                        const contract = activeContracts.find(c => c.id === data.proposal_open_contract.contract_id);
                        const status = data.proposal_open_contract.status;
                        if (status === 'sold' || status === 'won' || status === 'lost') {
                            const profit = parseFloat(data.proposal_open_contract.profit);
                            const isWin = profit > 0;
                            processTradeOutcome(contract, isWin);
                            activeContracts = activeContracts.filter(c => c.id !== contract.id);
                        }
                    }
                } else if (data.msg_type === 'subscription') {
                    subscriptionId = data.subscription.id;
                    addLog(`Subscribed to ticks with ID: ${subscriptionId}`);
                }
            } catch (e) {
                addLog(`Error processing message: ${e.message}`, 'error');
            }
        };
        
        ws.onclose = () => {
            updateConnectionStatus(false);
            addLog('WebSocket closed', 'warning');
            clearInterval(pingTimer);
            if (reconnectAttempts < MAX_RECONNECT_ATTEMPTS) {
                reconnectAttempts++;
                let delay = RECONNECT_DELAY * Math.pow(2, reconnectAttempts - 1); // exponential backoff
                addLog(`Reconnecting in ${delay/1000}s... (attempt ${reconnectAttempts})`, 'info');
                setTimeout(connectWebSocket, delay);
            } else {
                addLog('Max reconnection attempts reached. Please refresh.', 'error');
            }
        };
        
        ws.onerror = (err) => {
            addLog('WebSocket error - check connection', 'error');
        };
    }

    function subscribeToTicks() {
        if (ws && ws.readyState === WebSocket.OPEN) {
            if (subscriptionId) ws.send(JSON.stringify({ forget: subscriptionId }));
            ws.send(JSON.stringify({ ticks: currentContract.market, subscribe: 1 }));
            addLog(`Subscribed to ${currentContract.market} ticks`);
        }
    }

    function processTickData(tick) {
        // Validate tick data
        if (!tick || !tick.symbol || typeof tick.quote !== 'number') {
            addLog('Received invalid tick data', 'error');
            return;
        }
        const { symbol, quote, pip_size = 2 } = tick;
        if (symbol !== currentContract.market) return;
        currentPrice = quote;
        const pipSize = getPipSize(symbol);
        currentPriceDisplay.textContent = quote.toFixed(pipSize);

        lastFivePrices.push(quote);
        if (lastFivePrices.length > 5) lastFivePrices.shift();

        // Feed StepperBrain with throttling
        const scaled = Math.round(quote * 1000);
        stepper.processInput(scaled);

        // Update digits and quotes
        const lastDigit = Math.floor((quote % 1) * Math.pow(10, pipSize)) % 10;
        digits[symbol].unshift(lastDigit);
        if (digits[symbol].length > 4) digits[symbol].pop();

        const isTrigger = isTriggerQuote(symbol, quote, pipSize);
        quotes[symbol].unshift({ quote, pip_size: pipSize, isTrigger });
        if (quotes[symbol].length > 4) quotes[symbol].pop();
        updateQuoteDisplay(symbol);

        // ---- Simulation handling (fake contracts) ----
        if (pendingSimulation) {
            let isWin = false;
            if (currentContract.type === 'DIGITDIFF') {
                isWin = lastDigit !== pendingSimulation.barrier;
            } else if (currentContract.type === 'CALL' || currentContract.type === 'PUT') {
                if (typeof window.lastPrice !== 'undefined' && window.lastPrice !== null) {
                    let actualDir = quote > window.lastPrice ? 'CALL' : (quote < window.lastPrice ? 'PUT' : null);
                    isWin = (actualDir === pendingSimulation.predictedDirection);
                }
            } else {
                isWin = (lastDigit % 2) === pendingSimulation.barrier;
            }
            virtualOutcomes.push(isWin ? 'win' : 'loss');
            addLog(`Simulation result: fake ${isWin ? 'won' : 'loss'}`, 'info');
            
            if (stepper.masterMode) {
                stepper.recordFakeContract(
                    isWin ? 'win' : 'loss',
                    pendingSimulation.trigger || (pendingSimulation.barrier !== undefined ? pendingSimulation.barrier : (pendingSimulation.predictedDirection ? (quote - window.lastPrice) : 0)),
                    currentContract.type,
                    symbol,
                    lastFivePrices.slice(0,5)
                );
            }
            
            pendingSimulation = null;

            if (virtualOutcomes.length >= 3) {
                const last3 = virtualOutcomes.slice(-3);
                if (last3[0] === 'loss' && last3[1] === 'win' && last3[2] === 'win') {
                    isNextReal = true;
                    addLog('Pattern L W W detected - next trigger will be real', 'info');
                }
            }
        }

        // If bot is running and trigger detected
        if (isBotRunning && isTrigger) {
            addLog(`TRIGGER DETECTED: ${quote.toFixed(pipSize)} for ${symbol}`, 'warning');
            stepper.triggerHistory.push({ time: new Date(), quote, market: symbol, contractType: currentContract.type });

            const decimalStr = (quote % 1).toFixed(pipSize).substring(2);
            const midIndex = Math.floor((pipSize - 1) / 2);
            const middle = parseInt(decimalStr[midIndex] || '0', 10);

            if (currentContract.type === 'DIGITDIFF') {
                lastDiffersBarrier = middle;
                lastDiffersBarrierEl.textContent = String(lastDiffersBarrier);
                if (isStepperApplied || isMasterApplied) {
                    if (isNextReal) { purchaseDigitDiff(lastDiffersBarrier); isNextReal = false; }
                    else { pendingSimulation = { barrier: lastDiffersBarrier, trigger: quote }; addLog(`Simulating DIGITDIFF with barrier ${lastDiffersBarrier}`, 'info'); }
                } else { purchaseDigitDiff(lastDiffersBarrier); }
            }
            else if (currentContract.type === 'CALL' || currentContract.type === 'PUT') {
                let lastPrediction = stepper.getLastPrediction();
                let predictedPrice = lastPrediction ? lastPrediction / 1000 : null;
                let predictedDirection = predictedPrice ? (predictedPrice > currentPrice ? 'CALL' : 'PUT') : null;
                if (predictedDirection) {
                    addLog(`Stepper predicts next price: ${predictedPrice.toFixed(pipSize)} (${predictedDirection})`, 'info');
                }

                if (isMasterApplied && stepper.masterMode) {
                    const shouldBuy = stepper.decideTrade(quote, currentContract.type, symbol, lastFivePrices.slice(0,5));
                    if (shouldBuy === true) {
                        addLog(`Master strategy approves purchase for ${currentContract.type}`, 'info');
                        purchaseRiseFall(currentContract.type);
                    } else if (shouldBuy === false) {
                        addLog(`Master strategy rejects purchase for ${currentContract.type} (simulating loss)`, 'warning');
                        pendingSimulation = { predictedDirection: currentContract.type, trigger: quote };
                    } else {
                        addLog('Master strategy still learning (need 20 fake contracts)', 'warning');
                        pendingSimulation = { predictedDirection: currentContract.type, trigger: quote };
                    }
                }
                else if (isStepperApplied) {
                    if (isNextReal) { purchaseRiseFall(currentContract.type); isNextReal = false; }
                    else { pendingSimulation = { predictedDirection: currentContract.type, trigger: quote }; addLog(`Simulating ${currentContract.type}`, 'info'); }
                }
                else { purchaseRiseFall(currentContract.type); }
            }
            else {
                if (digits[symbol].length < 2) return;
                const prevLast = digits[symbol][1];
                const selectedParity = currentContract.type === 'DIGITODD' ? 1 : 0;
                const middleParity = middle % 2;
                const prevParity = prevLast % 2;
                if (prevParity === selectedParity && middleParity === selectedParity) {
                    if (isStepperApplied || isMasterApplied) {
                        if (isNextReal) { purchaseContract(); isNextReal = false; }
                        else { pendingSimulation = { barrier: selectedParity, trigger: quote }; addLog(`Simulating ${currentContract.type}`, 'info'); }
                    } else { purchaseContract(); }
                }
            }
        }

        window.lastPrice = quote;
        
        updatePatternDisplay();
        updateMetricsDisplay();
    }

    function updatePatternDisplay() {
        patternDisplay.innerHTML = '';
        const patterns = stepper.getPatterns();
        const patternKeys = Object.keys(patterns).slice(-5);
        patternKeys.forEach(key => {
            const pattern = patterns[key];
            const patternEl = document.createElement('div');
            patternEl.className = 'pattern-item';
            patternEl.textContent = `P${key}: ${pattern.contractType} ${pattern.outcome} @ ${new Date(pattern.timestamp).toLocaleTimeString()}`;
            patternDisplay.appendChild(patternEl);
        });
    }

    function updateMetricsDisplay() {
        metricsGrid.innerHTML = '';
        const metrics = stepper.getMetrics();
        const metricItems = [
            { name: 'Total Patterns', value: metrics.totalPatterns },
            { name: 'Fake Contracts', value: metrics.totalFake },
            { name: 'Real Contracts', value: metrics.totalReal },
            { name: 'Real Wins', value: metrics.wins },
            { name: 'Real Losses', value: metrics.losses },
            { name: 'Win Rate', value: metrics.winRate + '%' }
        ];
        metricItems.forEach(item => {
            const metricEl = document.createElement('div');
            metricEl.className = 'metric-item';
            metricEl.innerHTML = `<span>${item.name}:</span> <strong>${item.value}</strong>`;
            metricsGrid.appendChild(metricEl);
        });
    }

    // Backtesting function
    function runBacktest() {
        const market = backtestMarket.value;
        const ticks = parseInt(backtestTicks.value, 10);
        const strategy = backtestStrategy.value;
        const pipSize = getPipSize(market);
        
        // Generate synthetic price data (simple random walk)
        let prices = [10000]; // start price
        for (let i = 1; i < ticks; i++) {
            let change = (Math.random() - 0.5) * 20; // random step
            prices.push(prices[i-1] + change);
        }
        
        // Create a temporary stepper instance for backtest (or use existing? We'll use a new one to keep separate)
        const backtestStepper = new StepperBrain();
        if (strategy === 'master') {
            // For master, we need to copy patterns from main stepper? Optionally load from storage
            // For simplicity, we'll just use the current stepper's patterns if any
            // but to keep isolated, we'll run master only if ready in main stepper
            if (!stepper.masterReady) {
                addLog('Master strategy not ready in live instance; backtest may be inaccurate.', 'warning');
            }
        }
        
        let wins = 0, losses = 0, totalProfit = 0;
        let level = 0;
        let virtualOutcomesBT = [];
        let isNextRealBT = false;
        let pendingSimBT = null;
        let lastFive = [];
        let backtestLogEntries = [];
        
        for (let i = 0; i < prices.length; i++) {
            let price = prices[i];
            let scaled = Math.round(price * 1000);
            // Update last five
            lastFive.push(price);
            if (lastFive.length > 5) lastFive.shift();
            
            // Simulate trigger detection (simplified: use same trigger list)
            let frac = price - Math.floor(price);
            let trigger = parseFloat(frac.toFixed(pipSize));
            let isTrigger = triggerLists[market]?.some(t => Math.abs(t - trigger) < 0.001) || false;
            
            if (isTrigger) {
                // Simulate contract outcome
                let outcome = Math.random() > 0.5 ? 'win' : 'loss'; // 50/50 for demo
                if (strategy === 'master' && stepper.masterReady) {
                    // Use master decision
                    let shouldBuy = stepper.decideTrade(trigger, currentContract.type, market, lastFive);
                    if (shouldBuy === true) outcome = 'win';
                    else if (shouldBuy === false) outcome = 'loss';
                } else if (strategy === 'stepper') {
                    // LWW pattern logic
                    virtualOutcomesBT.push(outcome);
                    if (virtualOutcomesBT.length >= 3) {
                        let last3 = virtualOutcomesBT.slice(-3);
                        if (last3[0] === 'loss' && last3[1] === 'win' && last3[2] === 'win') {
                            isNextRealBT = true;
                        }
                    }
                    if (isNextRealBT) {
                        // real trade, use outcome as is
                        isNextRealBT = false;
                    } else {
                        // simulated, record but no profit impact
                        pendingSimBT = outcome;
                        outcome = null; // no real trade
                    }
                }
                
                if (outcome) {
                    let stake = martingaleSteps[level].stake;
                    let payout = martingaleSteps[level].payout;
                    if (outcome === 'win') {
                        wins++;
                        totalProfit += payout;
                        level = 0;
                    } else {
                        losses++;
                        totalProfit -= stake;
                        if (level < martingaleSteps.length - 1) level++;
                    }
                }
            }
        }
        
        let totalTrades = wins + losses;
        let winRate = totalTrades ? (wins / totalTrades * 100).toFixed(1) : 0;
        
        btTrades.textContent = totalTrades;
        btWins.textContent = wins;
        btLosses.textContent = losses;
        btWinRate.textContent = winRate + '%';
        btProfit.textContent = `$${totalProfit.toFixed(2)}`;
        
        backtestLog.innerHTML = `<div>Backtest completed on ${market} with ${ticks} ticks. Trades: ${totalTrades}, Win rate: ${winRate}%, Profit: $${totalProfit.toFixed(2)}</div>`;
    }

    // Event listeners
    setTokenBtn.addEventListener('click', () => {
        TOKEN = tokenInput.value.trim();
        if (TOKEN) {
            addLog('Token set. Connecting...', 'info');
            connectWebSocket();
        } else {
            addLog('Please enter a valid token', 'error');
        }
    });

    clearTokenBtn.addEventListener('click', () => {
        TOKEN = '';
        tokenInput.value = '';
        addLog('Token cleared', 'warning');
        if (ws) ws.close();
    });

    updateContractBtn.addEventListener('click', () => {
        const oldMarket = currentContract.market;
        currentContract.market = document.getElementById('market').value;
        currentContract.type = document.getElementById('contractType').value;
        currentContract.duration = parseInt(document.getElementById('duration').value);
        currentContract.takeProfit = parseFloat(document.getElementById('takeProfit').value);
        currentContract.stopLoss = parseFloat(document.getElementById('stopLoss').value);
        if (oldMarket !== currentContract.market && ws && ws.readyState === WebSocket.OPEN) subscribeToTicks();
        updateContractDisplay();
        addLog('Contract parameters updated');
    });

    testContractBtn.addEventListener('click', () => {
        addLog('Testing contract...', 'warning');
        const stake = martingaleSteps[currentMartingaleLevel].stake;
        const proposalRequest = {
            proposal: 1,
            amount: stake,
            basis: "stake",
            contract_type: currentContract.type,
            currency: "USD",
            duration: currentContract.duration,
            duration_unit: "t",
            symbol: currentContract.market
        };
        if (ws && ws.readyState === WebSocket.OPEN) ws.send(JSON.stringify(proposalRequest));
    });

    applyStepperBtn.addEventListener('click', () => {
        if (isStepperApplied) {
            isStepperApplied = false;
            applyStepperBtn.innerHTML = '<b><i>Apply Stepper Strategy</i></b>';
            addLog('Stepper strategy disabled', 'warning');
        } else {
            isStepperApplied = true;
            applyStepperBtn.innerHTML = '<b><i>Disable Stepper Strategy</i></b>';
            addLog('Stepper strategy enabled (L W W pattern -> real trade)', 'info');
        }
    });

    applyMasterBtn.addEventListener('click', () => {
        if (isMasterApplied) {
            isMasterApplied = false;
            applyMasterBtn.innerHTML = '<b><i>Apply Master Strategy</i></b>';
            stepper.disableMasterMode();
        } else {
            const dir = prompt('Enter a name for your data storage (e.g., "stepper_master_data"):', 'stepper_master_data');
            if (dir) {
                isMasterApplied = true;
                applyMasterBtn.innerHTML = '<b><i>Disable Master Strategy</i></b>';
                stepper.enableMasterMode(dir);
                addLog('Master strategy enabled. Learning from 20 fake contracts...', 'info');
            } else {
                addLog('Master strategy requires a storage name. Aborted.', 'error');
            }
        }
    });

    startBotBtn.addEventListener('click', () => {
        if (!isDerivConnected) { addLog('Please wait for connection', 'error'); return; }
        isBotRunning = true;
        startBotBtn.disabled = true;
        stopBotBtn.disabled = false;
        virtualOutcomes = [];
        isNextReal = false;
        pendingSimulation = null;
        addLog('Trading bot started with StepperBrain AI');
        addLog('Monitoring triggers and predicting movements...');
    });

    function stopBot() {
        isBotRunning = false;
        startBotBtn.disabled = false;
        stopBotBtn.disabled = true;
        addLog('Trading bot stopped');
    }
    stopBotBtn.addEventListener('click', stopBot);

    // Prediction frequency change
    predictionFrequencySelect.addEventListener('change', (e) => {
        stepper.setPredictionFrequency(e.target.value);
        addLog(`Prediction frequency set to every ${e.target.value} tick(s)`, 'info');
    });

    // Backtest toggle
    toggleBacktestBtn.addEventListener('click', () => {
        if (backtestSection.style.display === 'none') {
            backtestSection.style.display = 'block';
        } else {
            backtestSection.style.display = 'none';
        }
    });

    runBacktestBtn.addEventListener('click', runBacktest);

    exportBacktestBtn.addEventListener('click', () => {
        const data = {
            market: backtestMarket.value,
            ticks: backtestTicks.value,
            trades: btTrades.textContent,
            wins: btWins.textContent,
            losses: btLosses.textContent,
            winRate: btWinRate.textContent,
            profit: btProfit.textContent
        };
        const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
        const url = URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.href = url;
        a.download = 'backtest_results.json';
        a.click();
        URL.revokeObjectURL(url);
    });

    function initializeApp() {
        addLog('Initializing connection to Deriv API...');
        // Do not auto-connect; wait for token
        updateContractDisplay();
        MARKETS.forEach(m => { 
            quotes[m] = []; 
            digits[m] = []; 
            priceHistory[m] = []; 
            barData[m] = {close: []};
        });
        // Set default prediction frequency
        stepper.setPredictionFrequency(predictionFrequencySelect.value);
    }
    initializeApp();
</script>
</body>
</html>
