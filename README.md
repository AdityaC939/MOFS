# MOFS
Using computer simulations to find which "molecular sieves" (MOFs) could filter scarce helium out of natural gas, and then checking whether that filtering would actually work in the real world without using too much energy.

# Helium-sieving MOFs: screening and process model

Code for the CJSJ paper "Selectivity Is Not Enough". Everything runs on an ordinary laptop.
Total download is about 50 MB (the CoRE MOF 2019 database is installed as a Python package).

## Setup (once)
    pip install -r requirements.txt

## Run
    python process_model.py      # Fig. 1 and Table III (seconds)
    python step1_screen.py       # screening funnel -> screening_funnel.txt, candidates.csv (seconds)
    python step2_widom.py 5      # quick test on 5 MOFs (about a minute)
    python step2_widom.py        # all candidates (roughly 30-90 min; can be stopped and resumed)
    python step3_results.py      # prints Table II and summary numbers, saves ranked_candidates.csv

## Methods in brief
Pore-limiting diameters (PLD) and largest cavity diameters (LCD) are the Zeo++ values supplied
with CoRE MOF 2019 (all-solvent-removed, public). Henry coefficients are from Widom insertion:
rigid framework, UFF Lennard-Jones parameters, single-site He and TraPPE CH4 guests,
Lorentz-Berthelot mixing, 12.8 A cutoff, no charges, 298 K, 20,000 insertions per gas.

