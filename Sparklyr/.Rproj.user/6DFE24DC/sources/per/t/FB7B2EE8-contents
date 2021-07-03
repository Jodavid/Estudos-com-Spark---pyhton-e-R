#' -------------------------------------------------------
#' Estudos com sparklyr + dados parquet
#' 
#' Criado por: Jodavid Ferreira
#' Data de criação: 02.07.2021
#' 
#' Objetivo: Avançar nos estudos com R + spark
#' -------------------------------------------------------

#' -----------------------
#' Instalando o spark
#' -----------------------
# install.packages("sparklyr")
# remotes::install_github("GabeChurch/sparkedatools")

#' -----------------------
#' 1 Lendo as bibliotecas necessárias
#' -----------------------
library(sparklyr)
library(dplyr)
#' ---
library(e1071) # Para Skewness e Kurtosis
library(sparkedatools)
library(ggplot2)
#' -----------------------

#' ----------------------------------------------------------------------------

#' -----------------------
#' 2 Fazendo a conexão para o Spark Local
#' -----------------------
#sc <- spark_connect(master = "local",
#                    spark_home = "/home/hartbjf/spark-3.1.2-bin-hadoop3.2/")
sc <- try_spark_connect(master = "local",
                        spark_home = "/home/hartbjf/spark-3.1.2-bin-hadoop3.2/")

#' -----------------------
#' Lendo arquivos parquet
#' -----------------------
dados <- spark_read_parquet(sc, name = "../banco de dados - exemplo/userdata/" )

#' -----------------------
#' Verificando número de linhas
#' -----------------------
sdf_dim(dados)
sdf_nrow(dados)
sdf_ncol(dados)

#' ------------------------------------
#' Verificando as colunas
#' -----------------
colnames(dados)
sdf_schema(dados)
#' -----------------

#' ----------------------------------------------------------------------------

#' ------------------------------------
#' 3 Análise Exploratória - Descritiva
#' -----------------
colunas_selecionadas <- "salary"
#' ------
dados |> 
  select(colunas_selecionadas) |> 
    sdf_describe()
#' -----------------

#' ------------------------------------
#' Assimetria e Curtose
#' -----------------
dados |> 
  sdf_read_column(column = "salary") |> 
    skewness(na.rm = TRUE)
#' -----
dados |> 
  sdf_read_column(column = "salary") |> 
    kurtosis(na.rm = TRUE)
#' -----------------

#' ------------------------------------
#' Gerando um histograma
#' -----------------
salary <- dados |>
          select('salary') |>
          collect()

hist(salary$salary)
#' ------
ggplot(data = salary, aes(x = salary)) +
  geom_histogram(color="black")

#' -----------------
#' Gerando um BoxPlot
#' -----------------
salary <- dados |>
          select('salary') |>
          collect()
#' ------
ggplot(data = salary, aes(y = salary)) +
  geom_boxplot(color="black")
#' ------
ggplot(data = salary, aes(x = salary, y = salary)) +
  geom_violin(trim=FALSE, fill='#A4A4A4', color="darkred")
#' ------


