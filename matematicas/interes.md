## ELEMENTOS DE INTERES

1. **Capital inicial**
   
   (C="capital", K="kapital", vp="valor presente", va="valor actual")
   
   Es la cantidad de dinero prestado o invertido

2. **Interes**
   
   (I="interes")
   
   Es el valor(**dinero**) que se paga por el uso del dinero.

3. **Tasa de interes - Rédito**
   
   (i="interes", r="redito")
   
   **Porcentaje** que se paga por el dinero prestado o invertido

4. **Tiempo**
   
   (t="tiempo", n="numero de meses/años")
   
   Número de **periodos** que dura el prestamo o la inversion.

5. **Valor final - Monto**
   
   (vf="valor final", m="monto", Cf="capital final")
   
   ES la suma del capital más el interés.

---

## CONVERTIR PORCENTAJE

valor ejemplo: 2%

Convertir a decimal

$$
Decimal = \frac{n\%}{100}
$$

Decimal = 2/100 = 0.02

Convertir a porcentaje

$$
\% = ndecimal \times 100
$$

% = 0.02x100 = 2

---

## TIPO DE INTERES

1. **Interés simple**
   
   El interes **NO** se acumula al capital, genetalmente se paga periodo a periodo. 
   
   * El interes se paga con el mismo porcentaje mes a mes.
   
   * El interes siempre sera el mismo.
   
   * Si no se paga un mes, los intereses se sumas aparte
     
     es decir que el interes se acumula aparte 1.600+1.600 mas no al capital.
   
   **Hallar el capital inicial**
   
   Tengo que pagar 125.000 dentro de 5 meses, si el prestamo fue al 5% del interés simple mensual, ¿cuáto dinero me prestaron?
   
   vf(valor final) = 125.000
   
   t(tiempo) = 5 meses
   
   i(tasa de interes) = 5%
   
       Este tambien puede representarse en fracciones
   
           5% = 5/100 = 0.05
   
   c(capital) = x
   
   $$
   C = \frac{V_f}{1+ i \times t}
   $$
   
   C = 125000 / 1 + 0.05 x 5 = 100000 capital inicial
   
   **Hallar el interes simple**
   
   Se debe pagar un prestamo de $500000$ al 2% mensual durante 2 meses, ¿cuanto de interes se paga en estos 2 meses?
   
   c = 500000
   
   i = 2% mensual = 0.02
   
   t = 2 meses
   
   I = x 
   
   $$
   I = c \times i \times t
   $$
   
   I = 500000x0.02x2 = 20.000 de interes en 2 meses

2. **Interés compuesto - Interes efectivo - Interes sobre interes**
   
   Es el **interes** que se genera en **cada periodo** al agregar al capital inicial los intereses del periodo, generando un nuevo capital sobre el cual en el siguiente periodo se calcula un nuevo interés.
   
   * El capital cambia periodo a periodo
   
   * El interes cambia periodo a periodo
   
   * El valor final cambia periodo a periodo
   
   Capital = $100000$ 
   
   i = 10% anual
   
   t = 3 años]

| Año | capital | interes                                           | vf                                    |
| --- | ------- | ------------------------------------------------- | ------------------------------------- |
| 1   | 100.000 | 10.000 <br/>I1 =c1 x i<br/>I1=100.000x0.10=10.000 | 110.000<br/>Vf=100.000+10.000=110.000 |
| 2   | 110.000 | 11.000                                            | 121.000                               |
| 3   | 121.000 | 12.100                                            | 133.100                               |

   **FORMULA INTERES COMPUESTO**

* Interes compuesto
  
  $V_F = C (1 + i)⁺$

* Interes
  
  $I = C \times i$

* Valor final
  
  $V_f = C + I$

## CONVERSION DE TASAS DE INTERES

**TASA ANUAL**

| Nombre              | Símbolo     |     |
| ------------------- | ----------- | --- |
| Tasa Efectiva Anual | E.A \| T.EA |     |
| Tasa Efectiva Anual | T.E.A       |     |
| Tasa Anual          | Anual       |     |
| Tasa Año Vencido    | AV \| TAV   |     |

**TASA MENSUAL**

| Nombre                         | Símbolo  |     |
| ------------------------------ | -------- | --- |
| Tasa Mensual                   | mv \| MV |     |
| Tasa Mes Vencido               | mv \| MV |     |
| Tasa Efectiva Mensual          | TEM      |     |
| Tasa periódica Mensual         | TPM      |     |
| Tasa período mes vencido       | p.m.v    |     |
| Tasa períodica mensual vencida | p.m.v    |     |

**FORMULA**

Fórmula para convertir una tasa EA, a tasa periódica.

$$
ip = (1 + EA)¹^/n-1
$$

ip = intéres periódico - tasa periódica.

EA = Tasa Efectiva Anual

n = Número de períodos

| Tasa Periódica | n          |
| -------------- | ---------- |
| Diaria         | 360 \| 365 |
| Quincenal      | 24         |
| Mensual        | 12         |
| Bimestral      | 6          |
| Trimestral     | 3          |
| Cuatrimestral  | 4          |
| Semestral      | 2          |
| 45 días        | 360/45 = 8 |

Temas

* Amortizacion

* DIagrama de flujo de caja / flujo de efectivo
