# NTC Thermistor Calibration and Characterization

## 📌 Project Overview
This project documents the experimental calibration and dynamic characterization of a 2-pin NTC thermistor. The goal was to derive an accurate temperature-to-resistance transfer function and evaluate the sensor's transient response using a controlled water bath setup.

## 📊 Key Results

### 1. Sensor Sensitivity (Beta Calculation)
The thermistor's Beta ($\beta$) value was determined by plotting the natural log of resistance against inverse temperature.
- **Experimental Beta:** ~4950 K
- **Implication:** High sensitivity to temperature changes.

### 2. Static Calibration (Polynomial Model)
A 4th-degree polynomial was derived to convert Resistance ($\Omega$) directly to Temperature (K).
- **Model:** $T(K) = f(R)$ (4th Order)
- **Accuracy:** $R^2 = 0.990$
- **RMSE:** $\pm 1.50^\circ\text{C}$
- **Consistency:** Training RMSE (1.62 K) and Testing RMSE (1.25 K) were aligned, confirming no overfitting.

### 3. Dynamic Response
The sensor's response speed was tested via a step change ($0^\circ\text{C} \to 80^\circ\text{C}$).
- **Time Constant ($\tau$):** 6.25 seconds
- **Settling Time ($5\tau$):** ~31 seconds
- **Conclusion:** Suitable for steady-state monitoring; too slow for rapid transient tracking.

## 🧪 Methodology
1.  **Data Acquisition:** Used an Arduino-based voltage divider with a high-precision reference thermometer (Hg).
2.  **Hysteresis Control:** Averaged heating and cooling cycle resistance values.
3.  **Data Analysis:** Python (Pandas, Scikit-Learn, Scipy) was used for:
    -   Linear regression (Beta estimation).
    -   Polynomial feature transformation (Calibration curve).
    -   Exponential curve fitting (Time constant).

## 📂 Repository Structure
- `/data`: Raw resistance and voltage logs.
- `/scripts`: Python scripts for regression analysis and plotting.
- `/plots`: Generated calibration curves and residual plots.

## 🚀 Usage
To run the analysis script:
```bash
pip install pandas numpy matplotlib scikit-learn scipy
python calibration_analysis.py
