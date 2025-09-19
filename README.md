# PyPFD
Introduction

PyPFD is a Python library designed to calculate the Probability of Failure on Demand (PFD) in accordance with the international safety standards IEC 61508 and IEC 61511. It provides a way to estimate the reliability of Safety Devices, making it easier for engineers and safety professionals to perform consistent SIS assessments.

It allows you to evaluate PFDavg for various architectures (1oo1, 1oo2, 2oo2, 2oo3, 1oo3, and KooN using a general formula).

The library provides the following formulas:

def pfd_avg_1oo1(λ_du, λ_dd, T1_month, MTTR):

def pfd_avg_1oo1_pt(λ_du, λ_dd, T1_month, T2_month, PDC, MTTR):

def pfd_avg_1oo2(λ_du, λ_dd, β, βd, T1_month, MTTR):

def pfd_avg_1oo2_pt(λ_du, λ_dd, β, βd, T1_month, T2_month, PDC, MTTR):

def pfd_avg_1oo3(λ_du, λ_dd, β, βd, T1_month, MTTR):

def pfd_avg_2oo2(λ_du, λ_dd, T1_month, MTTR):

def pfd_avg_2oo2_pt(λ_du, λ_dd, T1_month, T2_month, PDC, MTTR):

def pfd_avg_2oo3(λ_du, λ_dd, β, βd, T1_month, MTTR):

def pfd_avg_KooN(K, N, λ_du, λ_dd, β, βd, T1_month, MTTR):

Parameters:

λ_du = dangerous undetected failure rate per hour

λ_dd = dangerous detected failure rate per hour

β = common cause for safe failure in %

βd = common cause for unsafe failure in %

T1_month = test interval in months (with PDC effectiveness)

T2_month = test interval in months for "as good as new" condition

PDC = partial diagnostic coverage of the test (% capable of revealing dangerous undetected failures)

MTTR = mean time to repair

All formulas assume identical devices. For combinations of different devices or different test intervals, see the formulas below (currently in development and not validated yet):

def pfhKooN(K, N, λ_d, β, T1_month):
def pfd_avg_1oo2_dif(λ_du1, λ_dd1, T1_month1, MTTR1, β1, βd1,
                      λ_du2, λ_dd2, T1_month2, MTTR2, β2, βd2):

def pfd_avg_2oo3_dif(λ_du1, λ_dd1, T1_month1, MTTR1, β1, βd1,
                      λ_du2, λ_dd2, T1_month2, MTTR2, β2, βd2,
                      λ_du3, λ_dd3, T1_month3, MTTR3, β3, βd3):

def pfd_avg_1oo3_dif(λ_du1, λ_dd1, T1_month1, MTTR1, β1, βd1,
                      λ_du2, λ_dd2, T1_month2, MTTR2, β2, βd2,
                      λ_du3, λ_dd3, T1_month3, MTTR3, β3, βd3):

Use example:

from PyPFD import PyPFDAvg

Print(PyPFDAvg.pfd_avg_2oo3(5E-8,0,0.02,0.01,12,8))

 4.57E-06

Print(PyPFDAvg.pfd_avg_KooN(2,3,5E-8,0,0.02,0.01,12,8))

 4.57E-06


Roadmap

-Test and validate all existing formulas.

-Create a GitHub repository explaining the logic behind the formulas.

-Develop default reliability data for common devices (Analog Transmitters, Valves, and Logic Solvers).


Highlights

-These formulas, combined with xlwings Lite in Excel, provide an efficient and user-friendly way to perform SIS assessments.

-If you need a specific architecture not present in the library, feel free to contact me for assistance.
