# Gillespie algorithm
 
Рассматриваемая модель авторепрессора:

$$\dot{x}=\displaystyle\frac{\alpha}{1+x^n}-x$$

## Алгоритм:

1.  Вычисление коэффициентов:

    1.1 считаем кинетические коэффициенты $r_i=\big[\displaystyle\frac{\alpha}{1+x^n};x\big]$

    $\displaystyle\frac{\alpha}{1+x^n}: \quad x\rightarrow x+1$ соотвествует образованию белка

    $x: \quad x\rightarrow x-1$ соотвествует разрушению белка
    
    1.2 Считаем общий кинетический коэффициент $\lambda = \displaystyle\sum_i r_i = \displaystyle\frac{\alpha}{1+x^n} + x $


2. Вычисление следующего времени реакции:

    2.1 генерируем случайное число $q_1\in [0,1]$ (равномерное распределение)

    2.2 Получаем $\tau = \displaystyle\frac{1}{\lambda}\ln{\displaystyle\frac{1}{q_1}} \rightarrow$ следующее время реакции


3. Выбор реакции:

    3.1 считаем вероятности образования реакций:

    $P(x\rightarrow x+1) = \displaystyle\frac{1}{\lambda} (\displaystyle\frac{\alpha}{1+x^n}) = P_1$
    
    $P(x\rightarrow x-1) = \displaystyle\frac{x}{\lambda} = P_2$

    3.2 Генерируем случайное число $q_2\in[0,1]$ :
   
   - если <span>$0 \lt q_2 \leq P_1 \Rightarrow x\rightarrow x+1$</span>
       
   - если <span>$P_1 \lt q_2 \leq P_1+P_2 \Rightarrow x\rightarrow x-1$</span>

5. Обновляем $x$ и $t$

6. Повторяем п. 1-4
