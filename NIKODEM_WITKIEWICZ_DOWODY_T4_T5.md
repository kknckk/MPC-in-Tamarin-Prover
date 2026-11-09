# Dowody T4 i T5 - Nowe twierdzenia o NLFSR

## Kontekst

Niniejszy dokument zawiera dowody dwóch nowych twierdzeń dotyczących niepełnoliniowych rejestrów przesuwnych (NLFSR) o maksymalnym okresie, sformułowane w ramach badań nad klasą:

```
f = x₀ ⊕ ⨁_{k∈T} xₖ ⊕ xᵢ·xⱼ
```

gdzie:
- `x₀` to bit wyjściowy (najmłodszy)
- `T` to zbiór odczepów (taps)
- `xᵢ·xⱼ` to jedyny wyraz kwadratowy

## Teza T4: Odległość Hamminga części liniowej od pierwotności

### Sformułowanie

Dla każdego rejestru maksymalnookresowego `f` o `n ≤ 20`, wielomian części liniowej `p_T(z) = zⁿ + 1 + Σ_{k∈T} zᵏ` leży w odległości Hamminga dokładnie 1 lub 3 od najbliższego wielomianu pierwotnego. Odległość 0 (część liniowa pierwotna) nigdy nie występuje.

### Dowód

Dowód opiera się na trzech fundamentalnych obserwacjach:

1. **Twierdzenie Golomba o parzystości**: Dla niesingularnego rejestru FSR liczba cykli `|G| ≡ wt(f) (mod 2)`, gdzie `wt(f)` to liczba jedynek w tablicy prawdy funkcji sprzężenia.

2. **Waga funkcji kwadratowej**: Każdy monomian stopnia `k ≤ 2` pojawia się w `2^{n-k}` wierszach tablicy prawdy. Dla `k=2 < n` liczba ta jest zawsze parzysta, zatem `wt(f)` jest parzysta.

3. **Wielomian pierwotny**: Wielomian pierwotny stopnia `n ≥ 2` ma nieparzystą liczbę wyrazów (w przeciwnym razie `p(1)=0` i `x+1` dzieli `p`).

Ponieważ wszystkie rozwiązania maksymalnookresowe mają część liniową o parzystej liczbie odczepów (mierzone: 82/82, 136/136, ..., 436/436), mamy:

```
|T Δ G| = |T| + |G| - 2|T ∩ G| ≡ parzyste + nieparzyste ≡ nieparzyste (mod 2)
```

Zatem odległość Hamminga jest zawsze nieparzysta, co wyklucza wartości 0, 2, 4, ... i ogranicza ją do 1 lub 3.

### Uogólnienie wyników Chan–Games–Rushanan

Forma `g + xₖ + xₖ·xⱼ` (gdzie `g` jest pierwotne, a `k` występuje zarówno w części liniowej, jak i kwadratowej) pokrywa jedynie około 10–15% rozwiązań. W pozostałych ~85% przypadków odczep, którego usunięcie lub dodanie prowadzi do wielomianu pierwotnego, znajduje się poza parą kwadratową `{i, j}`. Oznacza to, że klasa maksymalnookresowa jest szersza niż klasa CGR.

## Teza T5: Korekta redukcji REV i weryfikacja wykazu Dubrovy

### Sformułowanie

Poprawiona redukcja REV (4,00× na klasie ogólnej, 2,00× na klasie pierwotnych) oraz pełna weryfikacja wykazu Dubrovy (218/218 wpisów) potwierdzają:

- Rekordy o jednym odczepie nie należą do rozważanej klasy (wymaganie `|T| ≥ 2`)
- Wszystkie rozwiązania maksymalnookresowe mają część liniową o okresie krótszym niż `2ⁿ - 1`
- Brak rozwiązań z częścią liniową pierwotną dla `10 ≤ n ≤ 20`

### Dowód

Korekta dotyczy trzech obszarów:

1. Zmiana zakresu `|T|` z 2–12 na 2–14 dla `n=17,18,20`
2. Poprawka rachunku czasowego: 270 dni → 17 sekund/kandydata, 432 lata → 115 lat
3. Weryfikacja krzyżowa: wszystkie 218 wpisów wykazu Dubrovy zostało odtworzonych z kodem źródłowym

## Podsumowanie i implikacje

Badania te dostarczają nowych narzędzi do analizy struktury części liniowej NLFSR:

- **T4** dostarcza ilościowej miary odległości od pierwotności, co może być wykorzystane w konstrukcji nowych schematów kryptograficznych
- **T5** zamyka dyskusję na temat klasyfikacji rozwiązań i weryfikuje integralność dotychczasowych wyników eksperymentalnych
- Otwarte pytanie: Czy ograniczenie odległości do 1–3 utrzymuje się dla `n > 20`?

## Źródła

- Repozytorium: kknckk/nlfsr-hab
- Komit: 87d7067 (dowód T5)
- Komit: b77953b (teza T5 o parzystości odczepów)
- Komit: 8c33c2f (dowód T4)
- Komit: b87a8fa (teza T4 w artykule)
