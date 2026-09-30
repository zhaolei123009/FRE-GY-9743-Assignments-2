# FRE-GY 9743 — Assignment 2

Fixed-rate bond cashflows and Street yield pricing, NYU Fall 2026.

## Completed implementation

The six assigned methods in `fixedincomelib/analytics/bond_calculator.py` are
implemented: schedule generation, first/last/regular coupon accrual, accrued
interest, and yield-to-price with first and second yield derivatives.
The remaining calculator methods and supporting modules are unchanged.

Accrual dates are unadjusted; payment dates follow the supplied payment rules.
ICMA stubs use reference coupon periods, and first/interior/last periods use
their separately specified accrual bases. Regular coupons remain face times
annual coupon rate divided by frequency, as required by the assignment.
Multiple remaining payments use Street compound discounting; one remaining
payment uses simple discounting. Prices and interest use the supplied face
value, and yield inputs and derivatives use decimal annual yields.

Implementation follows the HW2 method instructions. The companion
[Assignment 3 bond calculator](https://github.com/Jerry0108-SJ/FRE-GY-9743-Assignments-3/blob/main/fixedincomelib/analytics/bond_calculator.py)
was used as an implementation reference.

## Run

Use Python 3.11 and the dependencies in `requirements.txt`:

```bash
python3.11 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter lab fixedincomelib/hw2_bondcalculator.ipynb
```

Open the notebook and choose **Restart Kernel and Run All Cells**.
The notebook already includes outputs from a fresh complete execution.

## Validation

Executed with Python 3.11.16, NumPy 1.26.4, pandas 2.3.1 and QuantLib 1.41.
All notebook cells and assertions passed:

- Introductory schedule agrees with the direct `qfCreateSchedule` API.
- All five supplied Bloomberg price and accrued-interest comparisons pass
  the assignment's rounding tolerances, including the special stub coupons.
- Analytic first/second yield derivatives match independent five-point
  finite differences for the introductory bond and all five Bloomberg cases.
- Clean-price-to-yield roundtrips recover the six input yields within 1e-9
  in decimal yield units.
- Ten additional checks cover forward/backward schedules, payment rolling,
  short/long ICMA first and final coupons, ACT/360 and ACT/365 FIXED,
  distinct period accrual bases, and zero accrued interest on a coupon date.

Bloomberg screenshots use face 1,000,000; the case calculations use face 100.
Multiply calculated amounts by 10,000 when comparing screenshot cash amounts.

## Upload to GitHub

Extract the submission ZIP first. Upload these files to their existing paths
in the Assignment 2 repository:

1. `fixedincomelib/analytics/bond_calculator.py`
2. `fixedincomelib/hw2_bondcalculator.ipynb`
3. `README.md`

With GitHub's web interface, navigate to each file's containing directory,
choose **Add file > Upload files**, and upload the corresponding file there.
This preserves the package structure and relative screenshot links.
All other original repository files are included unchanged in the ZIP.
