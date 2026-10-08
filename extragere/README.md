# Extragere

Câte un script Python pentru fiecare sursă. Scripturile doar descarcă și încarcă datele brute; transformările se fac în SQL, în `dbt/` (abordare ELT).

Convenție de nume: `extrage_<sursa>.py` (ex. `extrage_bilanturi_mf.py`).
Reguli: pauze între cereri, respectarea `robots.txt`, data descărcării salvată pentru fiecare fișier.
