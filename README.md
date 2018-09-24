# Aula-7


R version 3.5.1 (2018-07-02) -- "Feather Spray"
Copyright (C) 2018 The R Foundation for Statistical Computing
Platform: x86_64-w64-mingw32/x64 (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

> #Aula 7 - CritÃ©rios de InformaÃ§Ã£o
> 
> library(readxl)                                                        #Carrega os pacotes
> variacao_PIB <- read.table("c:/Econometria/Variacao.xls", header = T)  #Carrega os arquivos
Error in file(file, "rt") : cannot open the connection
In addition: Warning message:
In file(file, "rt") :
  cannot open file 'c:/Econometria/Variacao.xls': No such file or directory
> var_PIB <- ts(variacao_PIB$variacao_PIB, start =1951, frequency = 1 )  #Cria a serie temporal var_PIB
Error in is.data.frame(data) : object 'variacao_PIB' not found
> View(var_PIB)
Error in View : object 'var_PIB' not found
> plot(var_PIB, main="Variacao do PIB Brasileiro", col="Blue", ylab="%PIB", xlab="Ano")
Error in plot(var_PIB, main = "Variacao do PIB Brasileiro", col = "Blue",  : 
  object 'var_PIB' not found
> 
> acf(var_PIB)         #Cria a FAC -FunÃ§Ã£o de AutocorrelaÃ§Ã£o (ACF)
Error in as.ts(x) : object 'var_PIB' not found
> pacf(var_PIB)        #cria a FACP - FunÃ§ao de AutocorrelaÃ§Ã£o Parcial (PACF)
Error in pacf(var_PIB) : object 'var_PIB' not found
> 
> AR1 <- arima(var_PIB, order = c(1,0,0))   #Estima um modelo autoreressivo de ordem p=1 ,AR(1)
Error in NCOL(x) : object 'var_PIB' not found
> MA1 <- arima(var_PIB, order = c(0,0,1))   #Estima um modelo de mÃ©dias mÃ³veis ordem q=1 , MA(1)
Error in NCOL(x) : object 'var_PIB' not found
> ARMA11 <- arima(var_PIB, order = c(1,0,1))#Estima um modelo autoregressivo de mÃ©dias mÃ³veis ordem p=1 e q=1 ARMA(1,1)
Error in NCOL(x) : object 'var_PIB' not found
> 
> AIC(AR1) #Extrai a estatÃ�stica AIC do modelo AR1
Error in AIC(AR1) : object 'AR1' not found
> BIC(AR1) #Extrai a estatÃ�stica BIC Ddo modelo AR1
Error in BIC(AR1) : object 'AR1' not found
> 
> 
> AR2 <- arima(var_PIB, order = c(2,0,0))
Error in NCOL(x) : object 'var_PIB' not found
> 
> MA2 <- arima(var_PIB, order = c(0,0,2))
Error in NCOL(x) : object 'var_PIB' not found
> MA3 <- arima(var_PIB, order = c(0,0,3))
Error in NCOL(x) : object 'var_PIB' not found
> MA4
Error: object 'MA4' not found
> MA5
Error: object 'MA5' not found
> MA6
Error: object 'MA6' not found
> MA7
Error: object 'MA7' not found
> MA8
Error: object 'MA8' not found
> MA9
Error: object 'MA9' not found
> 
> ARMA12
Error: object 'ARMA12' not found
> ARMA13
Error: object 'ARMA13' not found
> ARMA14
Error: object 'ARMA14' not found
> ARMA15
Error: object 'ARMA15' not found
> ARMA16
Error: object 'ARMA16' not found
> ARMA17
Error: object 'ARMA17' not found
> ARMA18
Error: object 'ARMA18' not found
> ARMA19
Error: object 'ARMA19' not found
> 
> ARMA21
Error: object 'ARMA21' not found
> ARMA22
Error: object 'ARMA22' not found
> ARMA23
Error: object 'ARMA23' not found
> ARMA24
Error: object 'ARMA24' not found
> ARMA25
Error: object 'ARMA25' not found
> ARMA26
Error: object 'ARMA26' not found
> ARMA27
Error: object 'ARMA27' not found
> ARMA28
Error: object 'ARMA28' not found
> ARMA29
Error: object 'ARMA29' not found
> 
> #Exemplo aplicaÃ§Ã£o mÃºltipla - Extra (Deve-se completar as estimaÃ§Ãµes antes de executar esse cÃ³digo)
> 
> estimacoes <- list(AR1, AR2, MA1, MA2, MA3, MA4, MA5, MA6, MA7, MA8, MA9, 
+                    ARMA11,ARMA12, ARMA13, ARMA14,ARMA15, ARMA16,ARMA17,ARMA18,ARMA19,
+                    ARMA21,ARMA22,ARMA23,ARMA24,ARMA25,ARMA26,ARMA27,ARMA28,ARMA29)      #Cria uma lista com os estimadores
Error: object 'AR1' not found
> sapply(estimacoes, AIC)                 #Aplica o comando AIC na lista
Error in lapply(X = X, FUN = FUN, ...) : object 'estimacoes' not found
> sapply(estimacoes, BIC)                 #Aplica o comando BIC na lista
Error in lapply(X = X, FUN = FUN, ...) : object 'estimacoes' not found
> 
> #Exemplo de criaÃ§Ã£o de tabela com resultados - Extra
> AIC <- sapply(estimacoes, AIC) 
Error in lapply(X = X, FUN = FUN, ...) : object 'estimacoes' not found
> BIC <- sapply(estimacoes, BIC)
Error in lapply(X = X, FUN = FUN, ...) : object 'estimacoes' not found
> Modelo <- c("AR1", "AR2", "MA1", "MA2", "MA3", "MA4", "MA5", "MA6", "MA7", "MA8", "MA9", "ARMA11","ARMA12", "ARMA13", "ARMA14","ARMA15", "ARMA16","ARMA17","ARMA18","ARMA19","ARMA21","ARMA22","ARMA23","ARMA24","ARMA25","ARMA26","ARMA27","ARMA28","ARMA29")
> 
> Resultados <- data.frame(Modelo, AIC, BIC)
Error in as.data.frame.default(x[[i]], optional = TRUE) : 
  cannot coerce class ‘"function"’ to a data.frame
> View(Resultados)
Error in View : object 'Resultados' not found
