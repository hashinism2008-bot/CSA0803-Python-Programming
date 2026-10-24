# CSA0803-Python-Programming

Task1: data definition - inputs, named constants, types and validation rules.""" from decimal import Decimal

# Named constants (Decimal so money and percentages are exact)
 
BASE_RATE = Decimal("30.00")
STD_FAT = Decimal("3.5") STD_SNF = Decimal("8.5") FAT_STEP_VALUE = Decimal("0.40") SNF_STEP_VALUE = Decimal("0.30")
STEP = Decimal("0.1")
 
# Rs per litre at 3.5% fat and 8.5% SNF


# Rs per litre per 0.1% fat # Rs per litre per 0.1% SNF
 
MIN_FAT, MAX_FAT = Decimal("2.0"), Decimal("7.0")
MIN_SNF, MAX_SNF = Decimal("6.0"), Decimal("10.0") # assumption VALID_SHIFTS = ("M", "E")

# One sample entry showing the chosen data types entry = {
 
"farmer_id":	"F0123", "litres":	Decimal("8.5"),
"fat":	Decimal("4.2"),
"snf":	Decimal("8.7"), "shift": "M",
}
 
# str (identifier, not used in arithmetic) # Decimal
# Decimal # Decimal # str
 

def is_valid(e):
"""Return True when the entry satisfies every validation rule.""" return (bool(e["farmer_id"])
and e["litres"] >= 0
and MIN_FAT <= e["fat"] <= MAX_FAT and MIN_SNF <= e["snf"] <= MAX_SNF and e["shift"] in VALID_SHIFTS)

if   name  == "  main  ":
for key, value in entry.items():
print(f"{key:10} {value!r:12} {type(value).  name  }")
 
print("valid entry print("negative litres print("fat 7.5 (too high) print("shift 'X'
 
:", is_valid(entry))
:", is_valid({**entry, "litres": Decimal("-1")}))
:", is_valid({**entry, "fat": Decimal("7.5")}))
:", is_valid({**entry, "shift": "X"}))

# Task 2
>>> type(10), type(10.0), type("10"), type(True), type([10, 8.5])
(<class 'int'>, <class 'float'>, <class 'str'>, <class 'bool'>, <class 'list'>)
 
>>> 7 / 2
3.5
>>> 7 // 2
3
>>> 7 % 2
1
>>> -7 // 2
-4
 
# true division, always float # floor division
# remainder

# Task 3

Source: Task03/constants_demo.py
BASE_RATE = 30.00
 
STD_FAT = 3.5
STD_SNF = 8.5
FAT_STEP_VALUE = 0.40
SNF_STEP_VALUE = 0.30
STEP_SIZE = 0.1
MIN_FAT, MAX_FAT = 2.0, 7.0
RATE_CARD = {"base": 30.0, "fat": 0.40, "snf": 0.30}

# Task 4

import math
print("(4.2-3.5)/0.1 =", (4.2 - 3.5) / 0.1, "-> round:", round((4.2 - 3.5) / 0.1))
print("(3.1-3.5)/0.1 =", (3.1 - 3.5) / 0.1)
print("(8.7-8.5)/0.1 =", (8.7 - 8.5) / 0.1)
print("-2**2 =", -2 ** 2, " (-2)**2 =", (-2) ** 2, " 2**3**2 =", 2 ** 3 ** 2)
print("negatives: round(-2.5)=", round(-2.5), "int(-2.5)=", int(-2.5), "floor(-2.5)=", math.floor(-2.5))
BASE, FATV, SNFV = 30.0, 0.40, 0.30
for fat, snf in [(4.2, 8.5), (3.1, 8.5)]: raw = (fat - 3.5) / 0.1
for name, fn in [("round", round), ("int", int), ("floor", math.floor)]:
steps = fn(raw)
print(f"fat {fat}: raw={raw!r:20} {name:5} steps={steps:3} rate={BASE + steps*FATV:.2f}") fat = 4.2
print(2.0 <= fat <= 7.0, 2.0 <= fat and fat <= 7.0, not (fat < 2.0 or fat > 7.0))

# Task 5

def parse_float(text): try:
return float(text) except ValueError:
return None

def parse_with_string_checks(text): t = text.strip()
if t.replace(".", "", 1).isdigit(): return float(t)
return None

for s in ["8.5", "8,5", " 8.5 ", "eight"]:
print(f"{s!r:8} try/except -> {parse_float(s)!s:5} | string checks -> {parse_with_string_checks(s)}") amount = 283.9
print(f"[{amount:8.2f}] [{'F001':>6}] [{12:5d}]")
def read_float(prompt): 
    while True: 
      value = parse_float(input(prompt)) if value is not None:
return value
print("Invalid number, try again.")


# Task 6

BASE_RATE, FAT_STEP_VALUE,SNF_STEP_VALUE = 30.00, 0.40, 0.30

def rate_per_litre(fat, snf):
"""Return price per litre for the given fat and SNF percentage.""" fat_steps = round((fat - 3.5) / 0.1)
snf_steps = round((snf - 8.5) / 0.1)
return round(BASE_RATE + fat_steps * FAT_STEP_VALUE + snf_steps * SNF_STEP_VALUE, 2)

def payout(litres, fat, snf):
"""Return payment amount for one delivery.""" return round(litres * rate_per_litre(fat, snf), 2)

def ten_day_total(entries):
"""Return total payment for a farmer; entries = [(litres, fat, snf), ...].""" return round(sum(payout(l, f, s) for l, f, s in entries), 2)

if   name  == "  main  ":
week = [(10, 3.5, 8.5), (8.5, 4.2, 8.7), (12, 3.1, 8.3)]
print(ten_day_total(week)) square = lambda x: x * x print(square(4))

# Task 7

"""Rate card of thevillage milk co-operative."""

BASE_RATE	=	30.00
FAT_STEP_VALUE = 0.40
SNF_STEP_VALUE = 0.30

def rate_per_litre(fat, snf):
"""Return the price per litre, rounded to two decimals.""" fat_steps = round((fat - 3.5) / 0.1)
snf_steps = round((snf - 8.5) / 0.1)
return round(BASE_RATE + fat_steps * FAT_STEP_VALUE + snf_steps * SNF_STEP_VALUE, 2)

def payout(litres, fat, snf):
"""Return the payment amount rounded to two decimals.""" return round(litres * rate_per_litre(fat, snf), 2)

if   name  == "  main  ":
for litres, fat, snf in [(10, 3.5, 8.5), (8.5, 4.2, 8.7), (12, 3.1, 8.3)]:
rate = rate_per_litre(fat, snf) pay = payout(litres, fat, snf)
print(f"{litres:5} L fat {fat} snf {snf}" f" rate {rate:6.2f} pay {pay:8.2f}")

# Task 8
INPUT	litres, fat, snf OUTPUT rate, payment
CONSTANTS BASE_RATE = 30.00, FAT_STEP_VALUE = 0.40, SNF_STEP_VALUE = 0.30, STD_FAT = 3.5, STD_SNF = 8.5, STEP = 0.1, MIN_FAT = 2.0, MAX_FAT = 7.0
BEGIN
IF litres < 0 OR fat < MIN_FAT OR fat > MAX_FAT THEN DISPLAY "Invalid entry"
RETURN END IF
fatSteps <- ROUND((fat - STD_FAT) / STEP) snfSteps <- ROUND((snf - STD_SNF) / STEP)
rate	<- BASE_RATE + fatSteps * FAT_STEP_VALUE + snfSteps * SNF_STEP_VALUE payment	<- ROUND(litres * rate, 2)
RETURN rate, payment END

INPUT	entries (list of litres, fat, snf) OUTPUT total
BEGIN
total <- 0
FOR EACH entry IN entries DO IF entry is valid THEN
total <- total + CalculatePayment(entry.litres, entry.fat, entry.snf).payment
ELSE
DISPLAY "Entry skipped" END IF
END FOR
RETURN total END

# Task 9

BASE_RATE = Decimal("30.00") FAT_STEP_VALUE = Decimal("0.40") SNF_STEP_VALUE = Decimal("0.30")
STD_FAT, STD_SNF, STEP = Decimal("3.5"), Decimal("8.5"), Decimal("0.1") MIN_FAT, MAX_FAT = Decimal("2.0"), Decimal("7.0")
 
MIN_SNF, MAX_SNF = Decimal("6.0"), Decimal("10.0") PAISE = Decimal("0.01")
 
# assumption
 

def money(x):
return x.quantize(PAISE, rounding=ROUND_HALF_UP)

def parse_decimal(text):
"""Convert text to Decimal; raise ValueError for bad input (e.g. '8,5', 'eight').""" try:
value = Decimal(text.strip()) except Exception:
raise ValueError(f"not a number: {text!r}") if not value.is_finite():
raise ValueError(f"not a finite number: {text!r}") return value

def validate(litres, fat, snf): if litres < 0:
raise ValueError("litres must be non-negative") if not MIN_FAT <= fat <= MAX_FAT:
raise ValueError("fat must be between 2.0 and 7.0") if not MIN_SNF <= snf <= MAX_SNF:
raise ValueError("SNF must be between 6.0 and 10.0")

def steps(value, standard):
return ((value - standard) / STEP).to_integral_value(rounding=ROUND_HALF_UP)

def rate_per_litre(fat, snf):
return money(BASE_RATE + steps(fat, STD_FAT) * FAT_STEP_VALUE
+ steps(snf, STD_SNF) * SNF_STEP_VALUE)

def payout(litres, fat, snf):
return money(litres * rate_per_litre(fat, snf))

def ten_day_total(entries):
return sum((payout(l, f, s) for l, f, s in entries), Decimal("0.00"))

def process(litres_t, fat_t, snf_t):
l, f, s = parse_decimal(litres_t), parse_decimal(fat_t), parse_decimal(snf_t) validate(l, f, s)
return payout(l, f, s)
Source: Task09/test_calculator.py

from decimal import Decimal as D from milk_calc import *

cases = [
("above standard", ("8.5","4.2","8.7"), D("283.90")),
("below standard", ("12","3.1","8.3"), D("333.60")),
("boundary 3.5/8.5", ("10","3.5","8.5"), D("300.00")),
("lowest fat 2.0", ("10","2.0","8.5"), D("240.00")),
("highest fat 7.0", ("10","7.0","8.5"), D("440.00")),
("invalid text", ("10","eight","8.5"), ValueError),
("comma decimal", ("10","3,5","8.5"), ValueError),
("negative litres", ("-5","3.5","8.5"), ValueError),
("fat too high", ("10","7.1","8.5"), ValueError),
("fat too low", ("10","1.9","8.5"), ValueError),
 
]
print(f"{'Case':18}{'Input':26}{'Expected':>12}{'Actual':>12} for name, inp, exp in cases:
try:


# Task 10
import random, time
from decimal import Decimal, ROUND_HALF_UP random.seed(1)
P = Decimal("0.01")
def gen(n): # exact payments in 3 decimals, as products litres * rate can give return [Decimal(random.randint(10000, 60000)) / 1000 for _ in range(n)]
print(f"{'n':>8}{'float total':>22}{'Decimal total':>16}{'round each':>14}{'t_float(s)':>12}{'t_dec(s)':>10}") for n in (300, 6000, 150000):
data = gen(n); fl = [float(x) for x in data]
t = time.perf_counter(); tf = sum(fl); t_f = time.perf_counter() - t
t = time.perf_counter(); td = sum(data, Decimal(0)); t_d = time.perf_counter() - t each = sum((x.quantize(P, rounding=ROUND_HALF_UP) for x in data), Decimal(0))
print(f"{n:>8}{tf:>22.10f}{td.quantize(P, rounding=ROUND_HALF_UP):>16}{each:>14}{t_f:>12.6f}{t_d:>10.6f}") # rate-table vs recalculation
import sys; sys.path.insert(0, "../Task09")
from milk_calc import rate_per_litre def random_pair():
fat = Decimal(str(round(random.uniform(2, 7), 1)))
snf = Decimal(str(round(random.uniform(7, 9.5), 1))) return fat, snf
pairs = [random_pair() for _ in range(150000)]
t = time.perf_counter(); [rate_per_litre(f, s) for f, s in pairs]; t_calc = time.perf_counter() - t table = {}
t = time.perf_counter() for p in pairs:
if p not in table: table[p] = rate_per_litre(*p)
_ = table[p]
t_tab = time.perf_counter() - t
print(f"recalculate 150000: {t_calc:.3f}s | dict lookup: {t_tab:.3f}s | distinct pairs k = {len(table)}")

# Task 11

nil

# Task 12

import sys
sys.path.insert(0, "../Task07") import milkrate as old
import seasonal as new
from decimal import Decimal as D

print(f"{'fat':>5}{'snf':>6}{'raw fat steps':>22}{'old steps':>10}{'old rate':>10}{'new rate (normal)':>19}")
for fat, snf in [(4.25, 8.5), (4.35, 8.5), (4.45, 8.5), (4.15, 8.5), (3.55, 8.65)]:
raw = (fat - 3.5) / 0.1 print(f"{fat:>5}{snf:>6}{raw!r:>22}{round(raw):>10}{old.rate_per_litre(fat, snf):>10.2f}"
f"{new.money(new.rate_per_litre(D(str(fat)), D(str(snf)))):>19}") print("summer, original design cannot express: base 32.00 / fat step 0.45 / bonus")




