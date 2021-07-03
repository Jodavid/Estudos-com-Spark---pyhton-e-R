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

#' -----------------------
#' Lendo as bibliotecas necessárias
#' -----------------------
library(sparklyr)
library(dplyr)
#' -----------------------

#' -----------------------
#' Fazendo a conexão para o Spark Local
#' -----------------------
sc <- spark_connect(master = "local",
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

# ------------------------------------
# Verificando as colunas
# -----------------
colnames(dados)
sdf_schema(dados)
# -----------------
