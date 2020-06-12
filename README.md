# Implementação do Modelo Epidemiológico SIR utilizando Python.

## Modelo Epidemiológico **SIR**
A pandemia do COVID-19, também chamado de "o novo coronavírus", colocou em evidência a importância da matemática em nosso cotidiano. Tenho certeza que nesse período você já ouviu falar sobre projeções do avanço da doença e pico da curva de infectados. Porém, você sabe como a matemática se relaciona com esses termos?

<p align="center">
<img alt="covid" width="25%" src="https://github.com/eduardocorrearaujo/ModeloSIR/blob/master/imcovid.png?raw=true">
</p>
<center>
<a href="https://br.freepik.com/fotos-vetores-gratis/medico">Médico vetor criado por freepik - br.freepik.com</a>
</center>

Para compreender esses termos e realizar essas análise podemos utilizar modelos matemáticos, que são, a grosso modo, uma simplificação da realidade. No contexto de epidemias podem ser aplicados modelos compartimentais, que dividem a população em "caixinhas" para assim, tentar entender o comportamento de uma doença no decorrer do tempo. Um dos modelos compartimentais mais simples é o modelo epidemiológico **SIR**, proposto em 1927 por Kermack e McKendrick.

Esse modelo divide a população em 3 grupos, **Suscetíveis (S)**, **Infectados (I)** e **Recuperados (R)**. Suscetíveis  representam a parcela da população que
        não foi infectada, os infectados representam as pessoas que estão infectadas com o vírus, transmitindo para outras pessoas e os recuperados são aqueles que
        já se curaram, ou seja, estavam infectados, mas agora estão curados. Veja o diagrama abaixo.
<p align="center">
<img alt="sir" width="40%" src="https://github.com/eduardocorrearaujo/ModeloSIR/blob/master/modeloSIR.png?raw=true">
</p>

No digrama temos duas letras $\beta$ e $\gamma$ elas representam a taxa em que os indivíduos se movem de um grupo para o outro. O
$\beta$ representa a **taxa de contágio**, ela vai ser a responsável por "mover" uma pessoa do grupo dos suscetíveis para o grupo dos infectados. Ela está relacionada
a probabilidade de uma transmissão ocorrer decorrente do contato entre um indivíduo infectado e um indivíduo suscetível.  O $\gamma$ representa a **taxa  de recuperação**, ela é responsável por "mover"
o indivíduo do grupo dos infectados para o grupo dos recuperados. O inverso do $\gamma$, ($1/\gamma$) é muito importante, ele representa o **período infeccioso médio**, ou seja ele
nos fornece uma estimativa para quanto tempo o indivíduo estará infectando outras pessoas.

Matematicamente, o modelo SIR é definido pelo seguinte sistema de equações diferenciais ordinárias:

\begin{cases}
S'(t) = \dfrac{-\beta S(t) I(t)}{N}\\
I'(t) = \dfrac{\beta S(t) I(t)}{N} -  \gamma I(t)\\
R'(t) = \gamma I(t)
\end{cases}
                
Sendo $\beta$ a taxa de contágio, $\gamma$ a taxa de recuperação e $N$ a população total da região que estamos analisando. 

Esse modelo nos fornece uma informação muito importante sobre o desenvolvimento de uma epidemia. Ele nos fornece uma estimativa  da **taxa básica de
reprodução da doença/vírus**, que no caso do COVID-19 seria uma média de quantas pessoas podem ser infectadas por um indivíduo infectado em contato com os suscetíveis. Essa taxa é dada por $R_0 = \dfrac{\beta}{\gamma}$,
sendo importante ressaltar que $\dfrac{1}{\gamma}$ é o perído infeccioso médio e $\beta$ a taxa de contágio.

Veja no arquivo [SIR.ipynb](https://github.com/eduardocorrearaujo/ModeloSIR/blob/master/SIR.ipynb) como podemos implementar esse modelo utilizando a linguagem de programação **python**. Nesse caso, como esse modelo não tem solução analítica conhecida vamos utilizar o python para gerar uma solução númerica utilizando o comando `odeint` e vamos plotar essa solução utilizando a biblioteca `plotly`.
