- maior a b =
  if a > b then a else b

maior3 a b c =
  maior a (maior b c)

{-
  maior3 8 10 5 =
    maior 8 (maior 10 5) =
    maior 8 (if 10 > 5 then 10 else 5) =
    maior 8 (if True then 10 else 5) =
    maior 8 10 =
    if 8 > 10 then 8 else 10 =
    if False then 8 else 10 =
    10
-}

-- Definimos uma função para calcular o delta!
delta a b c =
  b * b - 4 * a * c

-- Assumindo que delta é positivo, calculamos a primeira raíz
primeiraRaiz a b c =
  (-b + sqrt (delta a b c)) / (2 * a)

-- Assumindo que delta é positivo, calculamos a segunda raíz
segundaRaiz a b c =
  (-b - sqrt (delta a b c)) / (2 * a)

-- Vamos juntar tudo! :)
bhaskara a b c =
  -- Nosso delta é não-negativo?
  if delta a b c >= 0 then
    -- Nosso delta é zero?
    if delta a b c == 0 then
      -- Uma única raíz real!
      [primeiraRaiz a b c]
    else
      -- Temos duas raízes reais!
      [primeiraRaiz a b c, segundaRaiz a b c]
  else
    -- Nenhuma raíz real :(
    []

{-
  Vamos, passo a passo, reduzir os valores!
  1) bhaskara 1 2 1 =
  2) if delta 1 2 1 >= 0 then
       if delta 1 2 1 == 0 then
         [primeiraRaiz 1 2 1]
       else
         [primeiraRaiz 1 2 1, segundaRaiz 1 2 1]
     else
       [] =
  
  3) if 0 >= 0 then
       if delta 1 2 1 == 0 then
         [primeiraRaiz 1 2 1]
       else
         [primeiraRaiz 1 2 1, segundaRaiz 1 2 1]
     else
       [] =
  4) if True then
       if delta 1 2 1 == 0 then
         [primeiraRaiz 1 2 1]
       else
         [primeiraRaiz 1 2 1, segundaRaiz 1 2 1]
     else
       [] =
    
  5) if delta 1 2 1 == 0 then
       [primeiraRaiz 1 2 1]
     else
       [primeiraRaiz 1 2 1, segundaRaiz 1 2 1] =
  
  6) if 0 == 0 then
       [primeiraRaiz 1 2 1]
     else
       [primeiraRaiz 1 2 1, segundaRaiz 1 2 1] =
  7) if True then
       [primeiraRaiz 1 2 1]
     else
       [primeiraRaiz 1 2 1, segundaRaiz 1 2 1] =
  
  8) [primeiraRaiz 1 2 1] =
  9) [-1.0]
  Chegamos ao resultado! :)
-}
