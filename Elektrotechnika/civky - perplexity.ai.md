# Cívky – základní informace a vzorce

---

## Co je cívka?

Cívka (induktor) je elektrická součástka, která ukládá energii v magnetickém poli vznikajícím kolem vodiče, kterým prochází elektrický proud. Cívka se obvykle skládá z drátu navinutého do spirály.

---

## Základní vlastnosti cívky

- **Indukčnost (L)** – schopnost cívky vytvářet magnetické pole a ukládat v něm energii. Měří se v henry (H).
- **Reaktance cívky (XL)** – odpor cívky vůči střídavému proudu, závisí na frekvenci.

---

## Základní vzorce

### 1. Indukčnost cívky

Indukčnost závisí na počtu závitů, délce a průřezu cívky a na materiálu jádra:

$$
L = \frac{\mu \cdot N^2 \cdot S}{l}
$$

kde:  
- $$L$$ = indukčnost (H)  
- $$\mu$$ = permeabilita materiálu jádra (H/m)  
- $$N$$ = počet závitů  
- $$S$$ = průřez cívky (m²)  
- $$l$$ = délka cívky (m)

---

### 2. Indukční reaktance

Reaktance cívky je odpor, který cívka klade střídavému proudu:

$$
X_L = 2 \pi f L
$$

kde:  
- $$X_L$$ = indukční reaktance (Ω)  
- $$f$$ = frekvence střídavého proudu (Hz)  
- $$L$$ = indukčnost (H)

---

### 3. Napětí na cívce

Napětí na cívce je úměrné změně proudu v čase:

$$
u = L \frac{d i}{d t}
$$

kde:  
- $$u$$ = napětí na cívce (V)  
- $$i$$ = proud (A)  
- $$\frac{d i}{d t}$$ = změna proudu v čase (A/s)

---

## Jak cívka funguje?

- Při změně proudu v cívce vzniká magnetické pole, které se mění.
- Změna magnetického pole indukuje v cívce napětí, které se snaží bránit změně proudu (tzv. elektromagnetická indukce).
- Proto cívka "brání" rychlým změnám proudu.

---

## Použití cívek

- Filtrace signálů (např. v rádiích)
- Vytváření elektromagnetických polí (transformátory, elektromagnety)
- V elektronických obvodech jako tlumivky nebo součástky ladicích obvodů
