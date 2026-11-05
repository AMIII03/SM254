# SM254 – Group Assignment: Quant Finance with Python

โค้ดประกอบรายงานกลุ่ม **"การวิเคราะห์เชิงปริมาณและการสร้างกลยุทธ์การลงทุนด้วย Python สำหรับพอร์ตจำลองเชิง Quant Finance"**
ใช้ข้อมูลจริงของหุ้นไทยจาก yfinance ตามลำดับ **EDA → Quantitative → Technical → Trading Strategy**

## ไฟล์ในโปรเจกต์

| ไฟล์ | เนื้อหา | ใช้กับ |
|---|---|---|
| [Part1_Python_Data.ipynb](Part1_Python_Data.ipynb) | 1.1 NumPy · 1.2 Pandas · 1.3 matplotlib / seaborn / mplfinance | รายงาน PDF ส่วนที่ 1 |
| [Part2_EDA.ipynb](Part2_EDA.ipynb) | 2.1 Data Overview · 2.2 Data Cleaning · 2.3 Descriptive · 2.4 Correlation · 2.5 Visualization | รายงาน PDF ส่วนที่ 2 |
| [Part3_Quant_Finance.ipynb](Part3_Quant_Finance.ipynb) | 3.1 ข้อมูลพื้นฐาน · 3.2 Fair Value · 3.3 Return · 3.4 Risk · 3.5 Markowitz, Monte Carlo, Efficient Frontier, CML, VaR | รายงาน PDF ส่วนที่ 3 |
| [Part4_Technical_Algo_Trading.ipynb](Part4_Technical_Algo_Trading.ipynb) | 4.1 Candlestick, SMA/EMA, MACD, RSI, Bollinger · กลยุทธ์ SMA Crossover, RSI Reversal, MACD Zero Line, BB Breakout | รายงาน PDF ส่วนที่ 4 |
| [Part6_Case_Study.ipynb](Part6_Case_Study.ipynb) | กรณีศึกษา: 16 หุ้น 4 อุตสาหกรรม → Fair Value → Return/Risk → เลือกตัวแทน → MPT พอร์ตที่ดีที่สุด + Monte Carlo 10,000 พอร์ต | **ไฟล์ .ipynb ที่ส่ง** |

> ส่วนที่ 5 (Reflection & Summary) สมาชิกแต่ละคนเขียนเองในรายงาน PDF คนละอย่างน้อย 1 หน้า A4 จึงไม่มีโค้ด

ทุก code cell มีคอมเมนต์ `#` อธิบายเป็นรายบรรทัด และทุกหัวข้อมีคำอธิบายผลเป็นภาษาไทย

## หุ้นที่ใช้

| กลุ่มอุตสาหกรรม | หุ้นที่วิเคราะห์ (ส่วนที่ 6) | ตัวแทนพอร์ต |
|---|---|---|
| Finance & Banking | KBANK, BBL, SCB, TTB | **KBANK** |
| Consumer & Retail | CPALL, CPN, BJC, CPAXT | **CPALL** |
| Energy & Utilities | OR, PTT, PTTEP, GPSC | **OR** |
| Transportation & Logistics | AOT, BEM, BTS, AAV | **AOT** |

- ส่วนที่ 1–4 ใช้ตัวแทนทั้ง 4 ตัว (KBANK, CPALL, OR, AOT)
- กลุ่ม Technology ในโจทย์เปลี่ยนเป็น Transportation เพื่อให้ใช้ AOT ได้
- MAKRO เปลี่ยนชื่อเป็น CPAXT ตั้งแต่ปี 2566 จึงใช้ `CPAXT.BK`

## สมมติฐานหลัก

| พารามิเตอร์ | ค่า | ใช้ทำอะไร |
|---|---|---|
| Risk-free rate (RF) | 2.0% ต่อปี | Sharpe Ratio, CML |
| Cost of equity (Ke) | 9.0% ต่อปี | DDM, Justified P/BV |
| Long-term growth (g) | 3.0% ต่อปี | DDM, Justified P/BV |
| วันทำการต่อปี | 252 | แปลงค่ารายวันเป็นรายปี |
| ค่าธรรมเนียมซื้อขาย | 0.15% ต่อครั้ง | Backtest ส่วนที่ 4 |

แก้ค่าเหล่านี้ได้ใน cell ตั้งค่าตอนต้นของแต่ละ notebook

## วิธีรัน

```bash
pip install yfinance pandas numpy matplotlib seaborn scipy mplfinance jupyter
```

```bash
jupyter notebook
```

แล้วเปิดไฟล์ notebook และกด **Run All** หรือเปิดบน Google Colab ก็ได้ (ไม่ต้องตั้งค่าเพิ่ม)

## หมายเหตุ

- ข้อมูลดึงสดจาก yfinance ทุกครั้งที่รัน ตัวเลขจึงเปลี่ยนตามวันที่รัน ผลลัพธ์ที่บันทึกไว้ในไฟล์มาจากการรันวันที่ **6 พ.ย. 2569** (ข้อมูล 5 พ.ย. 2568 – 4 พ.ย. 2569)
- ข้อความสรุปใน `Part6_Case_Study.ipynb` (หัวข้อ "การตีความเชิงกลยุทธ์") เขียนจากตัวเลขชุดนี้ ถ้ารันใหม่ต้องปรับตัวเลขในข้อความให้ตรง
- ส่วนที่ 4 ใช้ข้อมูล 2 ปีเพื่อให้ indicator (เช่น SMA50) มีข้อมูลตั้งต้น แล้ว backtest ในช่วง 1 ปีล่าสุด
- ผล backtest และพอร์ตที่ดีที่สุดเป็นแบบ in-sample ใช้เพื่อการศึกษา ไม่ใช่คำแนะนำการลงทุน

## กำหนดส่ง

- ส่งรายงาน PDF (ส่วนที่ 1–5) และไฟล์ `.ipynb` (ส่วนที่ 6) **ก่อนวันที่ 23 พฤศจิกายน 2569**
- นำเสนอกรณีศึกษาส่วนที่ 6 วันที่ **27 พฤศจิกายน 2569**
