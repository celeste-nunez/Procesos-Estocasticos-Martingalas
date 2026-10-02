# Procesos-Estocasticos-Martingalas
Simulación de martingalas en tiempo discreto y continuo: caminatas aleatorias, procesos de Poisson y Poisson compuesto, movimiento browniano, martingalas exponenciales e integral de Itô en Python. Para cada proceso se simulan trayectorias y se compara la media empírica con la esperanza teórica. Implementado en Python.

## Contenido

Todo está en `procesos_estocasticos_martingalas.ipynb`, en tres partes.

### Parte 1. Martingalas en tiempo discreto

| Proceso | Esperanza teórica |
|---|---:|
| Y_n = X_n² − n, con X_n caminata aleatoria simétrica | 0 |
| Transformada de martingala Y_n = Σ φ_k ξ_k con estrategia predecible | 0 |
| Y_n = ((1 − p)/p)^X_n, con X_n caminata asimétrica (p = 0.55) | 1 |

### Parte 2. Martingalas del proceso de Poisson

| Proceso | Esperanza teórica |
|---|---:|
| X_t = (N_t − λt)² − λt | 0 |
| Y_t = exp(N_t ln(1 − u) + uλt) | 1 |
| Poisson compensado X_t = N_t − λt | 0 |
| Martingala exponencial Y_t = exp(N_t − λt(e − 1)) | 1 |
| Poisson compuesto con saltos N(0, 4) | 0 |
| Poisson compuesto compensado Z_t = X_t − λt·E[Y], con saltos Gamma(5, 2) | 0 |

### Parte 3. Movimiento browniano

| Proceso | Esperanza teórica |
|---|---:|
| Martingala exponencial X_t = exp(cB_t − c²t/2) | 1 |
| B_t² − t | 0 |
| exp(B_t − t/2) | 1 |
| Y_t = tB_t − ∫₀ᵗ B_s ds | 0 |

Además, con 10,000 trayectorias se verifican propiedades del browniano:

| Cantidad | Simulación | Exacta |
|---|---:|---:|
| P(B_1 ≤ 0, B_2 ≤ 0) | 0.3729 | 0.3750 |
| P(∫₀¹ B_t dt > 2/√3) | 0.0206 | 0.0228 |
| Variación cuadrática en [0, 1] | 1.0000 | 1 |
| E[∫₀¹⁰ B_s dB_s] | 0.0079 | 0 |

La integral de Itô simulada coincide con la fórmula ∫₀¹⁰ B_s dB_s = ½B₁₀² − 5.

## Martingalas exponenciales

En las martingalas exponenciales, la media simulada cae muy por debajo de 1. No es un error: estos procesos tienden a 0 casi seguramente, pero conservan esperanza 1 gracias a trayectorias muy poco probables que alcanzan valores enormes y que no aparecen con pocas simulaciones. La martingala exponencial del browniano es la base del movimiento browniano geométrico con el que se modelan los precios de las acciones en Black-Scholes.

## Cómo usarlo

1. Clona el repositorio.
2. Instala las dependencias: `pip install numpy scipy matplotlib`
3. Abre `procesos_estocasticos_martingalas.ipynb` en Jupyter y ejecuta las celdas en orden.

## Herramientas

Python (NumPy, SciPy, Matplotlib).

## Autoría

Celeste Núñez López, con la colaboración de Ana Ximena Bravo Colin.
