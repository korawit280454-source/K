# K
K// Enhanced Stock search functionality with comprehensive database
        function initStockSearch() {
            const searchBox = document.getElementById('stockSearch');
            
            // Comprehensive stock database
            const stockDatabase = {
                // Tech Giants
                'AAPL': { name: 'Apple Inc.', sector: 'Technology', marketCap: '3.0T', pe: 28.5 },
                'MSFT': { name: 'Microsoft Corp.', sector: 'Technology', marketCap: '2.8T', pe: 32.1 },
                'GOOGL': { name: 'Alphabet Inc.', sector: 'Technology', marketCap: '1.7T', pe: 25.4 },
                'GOOG': { name: 'Alphabet Inc. (Class C)', sector: 'Technology', marketCap: '1.7T', pe: 25.2 },
                'AMZN': { name: 'Amazon.com Inc.', sector: 'Consumer Discretionary', marketCap: '1.5T', pe: 52.8 },
                'TSLA': { name: 'Tesla Inc.', sector: 'Consumer Discretionary', marketCap: '800B', pe: 65.2 },
                'NVDA': { name: 'NVIDIA Corp.', sector: 'Technology', marketCap: '1.1T', pe: 71.3 },
                'META': { name: 'Meta Platforms Inc.', sector: 'Communication Services', marketCap: '800B', pe: 24.7 },
                'NFLX': { name: 'Netflix Inc.', sector: 'Communication Services', marketCap: '200B', pe: 35.6 },
                'ADBE': { name: 'Adobe Inc.', sector: 'Technology', marketCap: '250B', pe: 41.2 },
                'CRM': { name: 'Salesforce Inc.', sector: 'Technology', marketCap: '220B', pe: 58.9 },
                'ORCL': { name: 'Oracle Corp.', sector: 'Technology', marketCap: '300B', pe: 28.7 },
                'INTC': { name: 'Intel Corp.', sector: 'Technology', marketCap: '150B', pe: 22.4 },
                'AMD': { name: 'Advanced Micro Devices', sector: 'Technology', marketCap: '200B', pe: 45.8 },
                'QCOM': { name: 'Qualcomm Inc.', sector: 'Technology', marketCap: '180B', pe: 18.2 },
                'TXN': { name: 'Texas Instruments Inc.', sector: 'Technology', marketCap: '160B', pe: 26.5 },
                'AVGO': { name: 'Broadcom Inc.', sector: 'Technology', marketCap: '550B', pe: 31.8 },
                
                // Financial Services
                'BRK.A': { name: 'Berkshire Hathaway (Class A)', sector: 'Financial Services', marketCap: '800B', pe: 9.8 },
                'BRK.B': { name: 'Berkshire Hathaway (Class B)', sector: 'Financial Services', marketCap: '800B', pe: 9.8 },
                'JPM': { name: 'JPMorgan Chase & Co.', sector: 'Financial Services', marketCap: '450B', pe: 12.5 },
                'BAC': { name: 'Bank of America Corp.', sector: 'Financial Services', marketCap: '280B', pe: 11.8 },
                'WFC': { name: 'Wells Fargo & Co.', sector: 'Financial Services', marketCap: '180B', pe: 12.9 },
                'GS': { name: 'Goldman Sachs Group', sector: 'Financial Services', marketCap: '120B', pe: 13.2 },
                'MS': { name: 'Morgan Stanley', sector: 'Financial Services', marketCap: '150B', pe: 14.1 },
                'C': { name: 'Citigroup Inc.', sector: 'Financial Services', marketCap: '100B', pe: 7.8 },
                'V': { name: 'Visa Inc.', sector: 'Financial Services', marketCap: '500B', pe: 32.4 },
                'MA': { name: 'Mastercard Inc.', sector: 'Financial Services', marketCap: '380B', pe: 33.1 },
                'PYPL': { name: 'PayPal Holdings Inc.', sector: 'Financial Services', marketCap: '80B', pe: 18.5 },
                'AXP': { name: 'American Express Co.', sector: 'Financial Services', marketCap: '120B', pe: 15.7 },
                
                // Healthcare
                'JNJ': { name: 'Johnson & Johnson', sector: 'Healthcare', marketCap: '450B', pe: 15.8 },
                'UNH': { name: 'UnitedHealth Group Inc.', sector: 'Healthcare', marketCap: '480B', pe: 24.2 },
                'PFE': { name: 'Pfizer Inc.', sector: 'Healthcare', marketCap: '200B', pe: 13.4 },
                'ABBV': { name: 'AbbVie Inc.', sector: 'Healthcare', marketCap: '280B', pe: 15.9 },
                'TMO': { name: 'Thermo Fisher Scientific', sector: 'Healthcare', marketCap: '220B', pe: 25.1 },
                'MRK': { name: 'Merck & Co. Inc.', sector: 'Healthcare', marketCap: '300B', pe: 16.7 },
                'LLY': { name: 'Eli Lilly and Co.', sector: 'Healthcare', marketCap: '650B', pe: 65.8 },
                'MDT': { name: 'Medtronic PLC', sector: 'Healthcare', marketCap: '110B', pe: 23.5 },
                
                // Consumer & Retail
                'WMT': { name: 'Walmart Inc.', sector: 'Consumer Staples', marketCap: '480B', pe: 26.8 },
                'HD': { name: 'Home Depot Inc.', sector: 'Consumer Discretionary', marketCap: '350B', pe: 22.1 },
                'PG': { name: 'Procter & Gamble Co.', sector: 'Consumer Staples', marketCap: '350B', pe: 24.5 },
                'KO': { name: 'Coca-Cola Co.', sector: 'Consumer Staples', marketCap: '260B', pe: 23.8 },
                'PEP': { name: 'PepsiCo Inc.', sector: 'Consumer Staples', marketCap: '230B', pe: 25.2 },
                'MCD': { name: 'McDonald\'s Corp.', sector: 'Consumer Discretionary', marketCap: '200B', pe: 24.9 },
                'NKE': { name: 'Nike Inc.', sector: 'Consumer Discretionary', marketCap: '150B', pe: 31.2 },
                'COST': { name: 'Costco Wholesale Corp.', sector: 'Consumer Staples', marketCap: '300B', pe: 44.7 },
                'TGT': { name: 'Target Corp.', sector: 'Consumer Discretionary', marketCap: '70B', pe: 15.8 },
                'LOW': { name: 'Lowe\'s Companies Inc.', sector: 'Consumer Discretionary', marketCap: '150B', pe: 21.3 },
                
                // Energy & Materials
                'XOM': { name: 'Exxon Mobil Corp.', sector: 'Energy', marketCap: '450B', pe: 14.2 },
                'CVX': { name: 'Chevron Corp.', sector: 'Energy', marketCap: '280B', pe: 15.1 },
                'COP': { name: 'ConocoPhillips', sector: 'Energy', marketCap: '140B', pe: 12.8 },
                'SLB': { name: 'Schlumberger NV', sector: 'Energy', marketCap: '70B', pe: 18.9 },
                
                // Industrial & Aerospace
                'BA': { name: 'Boeing Co.', sector: 'Industrials', marketCap: '120B', pe: -28.5 },
                'CAT': { name: 'Caterpillar Inc.', sector: 'Industrials', marketCap: '140B', pe: 16.4 },
                'GE': { name: 'General Electric Co.', sector: 'Industrials', marketCap: '160B', pe: 22.7 },
                'MMM': { name: '3M Co.', sector: 'Industrials', marketCap: '60B', pe: 12.9 },
                'HON': { name: 'Honeywell International', sector: 'Industrials', marketCap: '140B', pe: 24.8 },
                
                // Real Estate & Utilities
                'NEE': { name: 'NextEra Energy Inc.', sector: 'Utilities', marketCap: '150B', pe: 22.4 },
                'DUK': { name: 'Duke Energy Corp.', sector: 'Utilities', marketCap: '80B', pe: 19.8 },
                'SO': { name: 'Southern Co.', sector: 'Utilities', marketCap: '75B', pe: 20.1 },
                
                // Emerging/Growth Stocks
                'PLTR': { name: 'Palantir Technologies', sector: 'Technology', marketCap: '35B', pe: 180.5 },
                'SNOW': { name: 'Snowflake Inc.', sector: 'Technology', marketCap: '50B', pe: -85.2 },
                'ROKU': { name: 'Roku Inc.', sector: 'Communication Services', marketCap: '5B', pe: -8.9 },
                'SPOT': { name: 'Spotify Technology SA', sector: 'Communication Services', marketCap: '30B', pe: 125.4 },
                'SQ': { name: 'Block Inc.', sector: 'Financial Services', marketCap: '40B', pe: 38.7 },
                'SHOP': { name: 'Shopify Inc.', sector: 'Technology', marketCap: '80B', pe: 85.3 },
                'ZM': { name: 'Zoom Video Communications', sector: 'Technology', marketCap: '20B', pe: 18.9 },
                'UBER': { name: 'Uber Technologies Inc.', sector: 'Technology', marketCap: '120B', pe: 45.6 },
                'LYFT': { name: 'Lyft Inc.', sector: 'Technology', marketCap: '6B', pe: -12.4 },
                'ABNB': { name: 'Airbnb Inc.', sector: 'Consumer Discretionary', marketCap: '90B', pe: 18.2 },
                'DASH': { name: 'DoorDash Inc.', sector: 'Consumer Discretionary', marketCap: '50B', pe: -42.1 },
                
                // Biotech & Pharma
                'GILD': { name: 'Gilead Sciences Inc.', sector: 'Healthcare', marketCap: '90B', pe: 11.8 },
                'AMGN': { name: 'Amgen Inc.', sector: 'Healthcare', marketCap: '140B', pe: 15.2 },
                'BIIB': { name: 'Biogen Inc.', sector: 'Healthcare', marketCap: '35B', pe: 14.5 },
                'REGN': { name: 'Regeneron Pharmaceuticals', sector: 'Healthcare', marketCap: '90B', pe: 16.8 },
                'VRTX': { name: 'Vertex Pharmaceuticals', sector: 'Healthcare', marketCap: '110B', pe: 26.4 },
                
                // ETFs
                'SPY': { name: 'SPDR S&P 500 ETF Trust', sector: 'ETF', marketCap: '400B', pe: 0 },
                'QQQ': { name: 'Invesco QQQ Trust', sector: 'ETF', marketCap: '200B', pe: 0 },
                'IWM': { name: 'iShares Russell 2000 ETF', sector: 'ETF', marketCap: '60B', pe: 0 },
                'VTI': { name: 'Vanguard Total Stock Market', sector: 'ETF', marketCap: '300B', pe: 0 },
                'VOO': { name: 'Vanguard S&P 500 ETF', sector: 'ETF', marketCap: '350B', pe: 0 }
            };

            let searchTimeout;
            
            searchBox.addEventListener('input', function() {
                const query = this.value.trim();
                const watchlist = document.getElementById('watchlist');
                
                // Clear previous timeout
                clearTimeout(searchTimeout);
                
                if (query.length < 1) {
                    showDefaultWatchlist();
                    return;
                }
                
                // Add loading state
                watchlist.innerHTML = '<div style="text-align: center; padding: 20px; color: #666;"><div class="loading"></div> กำลังค้นหา...</div>';
                
                // Debounce search
                searchTimeout = setTimeout(() => {
                    performSearch(query, watchlist, stockDatabase);
                }, 300);
            });
            
            // Show default watchlist on page load
            showDefaultWatchlist();
        }
        
        function showDefaultWatchlist() {
            const watchlist = document.getElementById('watchlist');
            const defaultStocks = [
                { symbol: 'AAPL', name: 'Apple Inc.', price: 175.43, change: 2.15 },
                { symbol: 'TSLA', name: 'Tesla Inc.', price: 238.59, change: 8.42 },
                { symbol: 'NVDA', name: 'NVIDIA Corp.', price: 421.89, change: 12.73 },
                { symbol: 'MSFT', name: 'Microsoft Corp.', price: 338.11, change: -1.24 },
                { symbol: 'GOOGL', name: 'Alphabet Inc.', price: 129.87, change: 3.45 }
            ];
            
            watchlist.innerHTML = '';
            defaultStocks.forEach(stock => {
                const changePercent = (stock.change / stock.price * 100).toFixed(2);
                const item = document.createElement('div');
                item.className = 'watchlist-item';
                item.innerHTML = `
                    <div>
                        <div class="stock-symbol">${stock.symbol}</div>
                        <div class="stock-name">${stock.name}</div>
                    </div>
                    <div class="stock-price">
                        <div class="stock-price-value">$${stock.price}</div>
                        <div class="stock-change ${stock.change > 0 ? 'positive' : 'negative'}">${stock.change > 0 ? '+' : ''}${stock.change} (${changePercent}%)</div>
                    </div>
                `;
                item.addEventListener('click', () => showStockDetail(stock.symbol));
                watchlist.appendChild(item);
            });
        }
        
        function performSearch(query, watchlist, stockDatabase) {
            const queryUpper = query.toUpperCase();
            const results = [];
            
            // Search by symbol and name
            Object.keys(stockDatabase).forEach(symbol => {
                const stock = stockDatabase[symbol];
                const symbolMatch = symbol.includes(queryUpper);
                const nameMatch = stock.name.toUpperCase().includes(queryUpper);
                const sectorMatch = stock.sector.toUpperCase().includes(queryUpper);
                
                if (symbolMatch || nameMatch || sectorMatch) {
                    results.push({
                        symbol: symbol,
                        ...stock,
                        relevance: symbolMatch ? 3 : (nameMatch ? 2 : 1)
                    });
                }
            });
            
            // Sort by relevance
            results.sort((a, b) => b.relevance - a.relevance);
            
            watchlist.innerHTML = '';
            
            if (results.length === 0) {
                watchlist.innerHTML = `
                    <div style="text-align: center; padding: 20px; color: #666;">
                        <i class="fas fa-search"></i><br>
                        ไม่พบหุ้นที่ค้นหา "${query}"<br>
                        <small>ลองใช้ชื่อบริษัทหรือสัญลักษณ์หุ้น</small>
                    </div>
                `;
                return;
            }
            
            // Limit results to top 10
            results.slice(0, 10).forEach(stock => {
                const item = document.createElement('div');
                item.className = 'watchlist-item';
                
                // Generate realistic price data
                const price = generateRealisticPrice(stock.symbol, stock.marketCap);
                const change = (Math.random() * 20 - 10).toFixed(2);
                const changePercent = (change / price * 100).toFixed(2);
                
                item.innerHTML = `
                    <div style="flex: 1;">
                        <div style="display: flex; align-items: center; gap: 0.5rem;">
                            <div class="stock-symbol">${stock.symbol}</div>
                            <div style="background: ${getSectorColor(stock.sector)}; color: white; padding: 2px 6px; border-radius: 10px; font-size: 0.7rem;">${stock.sector}</div>
                        </div>
                        <div class="stock-name">${stock.name}</div>
                        <div style="font-size: 0.7rem; color: #888; margin-top: 2px;">
                            Cap: ${stock.marketCap} | P/E: ${stock.pe > 0 ? stock.pe : 'N/A'}
                        </div>
                    </div>
                    <div class="stock-price">
                        <div class="stock-price-value">$${price}</div>
                        <div class="stock-change ${change > 0 ? 'positive' : 'negative'}">${change > 0 ? '+' : ''}${change} (${changePercent}%)</div>
                    </div>
                `;
                
                // Add click handler for stock details
                item.addEventListener('click', () => showStockDetail(stock.symbol));
                
                // Add to watchlist button
                const addBtn = document.createElement('div');
                addBtn.innerHTML = '<i class="fas fa-plus"></i>';
                addBtn.style.cssText = 'position: absolute; top: 5px; right: 5px; background: rgba(30,60,114,0.1); border-radius: 50%; width: 25px; height: 25px; display: flex; align-items: center; justify-content: center; cursor: pointer; opacity: 0; transition: opacity 0.3s ease;';
                addBtn.onclick = (e) => {
                    e.stopPropagation();
                    addToWatchlist(stock.symbol, stock.name);
                };
                
                item.style.position = 'relative';
                item.addEventListener('mouseenter', () => addBtn.style.opacity = '1');
                item.addEventListener('mouseleave', () => addBtn.style.opacity = '0');
                item.appendChild(addBtn);
                
                watchlist.appendChild(item);
            });
            
            // Add search suggestions at the bottom
            if (results.length > 10) {
                const moreResults = document.createElement('div');
                moreResults.style.cssText = 'text-align: center; padding: 10px; color: #666; font-size: 0.9rem; border-top: 1px solid #eee;';
                moreResults.innerHTML = `<i class="fas fa-info-circle"></i> แสดงแล้ว 10 จาก ${results.length} ผลลัพธ์`;
                watchlist.appendChild(moreResults);
            }
        }
        
        function getSectorColor(sector) {
            const colors = {
                'Technology': '#667eea',
                'Healthcare': '#00cec9',
                'Financial Services': '#fdcb6e',
                'Consumer Discretionary': '#e17055',
                'Consumer Staples': '#00b894',
                'Communication Services': '#a29bfe',
                'Industrials': '#fd79a8',
                'Energy': '#f39c12',
                'Utilities': '#55a3ff',
                'Materials': '#26de81',
                'Real Estate': '#ff7675',
                'ETF': '#74b9ff'
            };
            return colors[sector] || '#95a5a6';
        }
        
        function generateRealisticPrice(symbol, marketCap) {
            const capMultiplier = marketCap.includes('T') ? 100 : marketCap.includes('B') ? 10 : 1;
            const basePrice = Math.random() * 300 * capMultiplier + 50;
            return Math.max(10, basePrice).toFixed(2);
        }
        
        function addToWatchlist(symbol, name) {
            // Show confirmation
            const notification = document.createElement('div');
            notification.innerHTML = `<i class="fas fa-check"></i> เพิ่ม ${symbol} ลงใน Watchlist แล้ว`;
            notification.style.cssText = `
                position: fixed; 
                top: 120px; 
                right: 20px; 
                background: rgba(0, 255, 136, 0.9); 
                color: white;
                padding: 12px 20px; 
                border-radius: 25px; 
                box-shadow: 0 8px 25px rgba(0,255,136,0.3); 
                z-index: 1000; 
                font-size: 0.9rem;
                animation: slideInRight 0.5s ease;
            `;
            document.body.appendChild(notification);
            
            setTimeout(() => {
                if (notification.parentNode) {
                    document.body.removeChild(notification);
                }
            }, 3000);
        }
        
        function showStockDetail(symbol) {
            // Create detailed stock modal
            const modal = document.createElement('div');
            modal.style.cssText = `
                position: fixed; 
                top: 0; 
                left: 0; 
                width: 100%; 
                height: 100%; 
                background: rgba(0,0,0,0.8); 
                z-index: 2000; 
                display: flex; 
                align-items: center; 
                justify-content: center;
                animation: fadeIn 0.3s ease;
            `;
            
            modal.innerHTML = `
                <div style="background: white; border-radius: 20px; padding: 2rem; max-width: 600px; width: 90%; max-height: 80%; overflow-y: auto; box-shadow: 0 20px 60px rgba(0,0,0,0.3);">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 2rem;">
                        <h2 style="color: #1e3c72; margin: 0;">${symbol} - รายละเอียดหุ้น</h2>
                        <button onclick="this.parentElement.parentElement.parentElement.remove()" style="background: none; border: none; font-size: 1.5rem; cursor: pointer; color: #666;">×</button>
                    </div>
                    <div id="stockDetailContent">
                        <div style="text-align: center; padding: 40px;">
                            <div class="loading"></div>
                            <p>กำลังโหลดข้อมูล...</p>
                        </div>
                    </div>
                </div>
            `;
            
            document.body.appendChild(modal);
            
            // Simulate loading stock details
            setTimeout(() => {
                const content = document.getElementById('stockDetailContent');
                if (content) {
                    content.innerHTML = `
                        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; margin-bottom: 2rem;">
                            <div>
                                <h3 style="color: #1e3c72;">ราคาปัจจุบัน</h3>
                                <div style="font-size: 2rem; font-weight: 700; color: #333;">$${generateRealisticPrice(symbol, '100B')}</div>
                                <div style="color: #00ff88; font-weight: 600;">+$5.47 (+2.31%)</div>
                            </div>
                            <div>
                                <h3 style="color: #1e3c72;">สถิติ</h3>
                                <div style="font-size: 0.9rem; line-height: 1.8;">
                                    <div>วอลลุ่มวันนี้: 45.2M</div>
                                    <div>ช่วงวันนี้: $${(Math.random() * 10 + 140).toFixed(2)} - $${(Math.random() * 10 + 180).toFixed(2)}</div>
                                    <div>52 สัปดาห์: $${(Math.random() * 50 + 100).toFixed(2)} - $${(Math.random() * 50 + 200).toFixed(2)}</div>
                                </div>
                            </div>
                        </div>
                        <div style="background: linear-gradient(135deg, rgba(30,60,114,0.1), rgba(102,126,234,0.1)); border-radius: 15px; padding: 1.5rem; margin-bottom: 1.5rem;">
                            <h3 style="color: #1e3c72; margin-bottom: 1rem;">AI Analysis</h3>
                            <p style="line-height: 1.6; margin: 0;">หุ้น ${symbol} แสดงแนวโน้มในเชิงบวกจากการวิเคราะห์ทางเทคนิค โดยมีการรองรับที่ระดับ $${(Math.random() * 20 + 160).toFixed(2)} และความต้านทานที่ $${(Math.random() * 20 + 190).toFixed(2)} คาดการณ์ราคาเป้าหมาย 7 วัน: $${(Math.random() * 30 + 200).toFixed(2)}</p>
                        </div>
                        <div style="display: flex; gap: 1rem;">
                            <button onclick="addToWatchlist('${symbol}', 'Company Name')" style="background: linear-gradient(135deg, #667eea, #764ba2); color: white; border: none; padding: 0.8rem 1.5rem; border-radius: 25px; cursor: pointer; font-weight: 600;">
                                <i class="fas fa-plus"></i> เพิ่มใน Watchlist
                            </button>
                            <button style="background: linear-gradient(135deg, #00ff88, #00d4aa); color: white; border: none; padding: 0.8rem 1.5rem; border-radius: 25px; cursor: pointer; font-weight: 600;">
                                <i class="fas fa-chart-line"></i> ดูกราฟ
                            </button>
                        </div>
                    `;
                }
            }, 1500);
            
            // Close modal when clicking outside
            modal.addEventListener('click', (e) => {
                if (e.target === modal) {
                    document.body.removeChild(modal);
                }
            });
        }
