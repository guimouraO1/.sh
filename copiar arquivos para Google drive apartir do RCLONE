#!/bin/bash

###########################################################################
#        Script para copiar arquivos para uma pasta em nuvem GOES-16      #
###########################################################################
#  Metodo: Diario                                                         #
#  Descricao: Script para copiar apenas o dia anterior para uma pasta em  #
#  nuvem GOES-16                                                          #
#  Autor: Guilherme de Moura Oliveira  <guimoura@unicamp.br>              #
#  Data: 9/05/2023                                                        #
#  Atualizacao: 10/05/2023                                                #
###########################################################################

ARQ_LOG="BKP_GOES-R_LEVEL2`date +%Y-%m-%d`.log"
DIR_LOG=/Scripts/backup_logs/

#Obtendo o ano e dia anterior em dia juliano
ano=$(date +%Y -d "-1 day")
dia_anterior=$(date +%j -d "-1 day")

# ano=2024
# dia_anterior=001

# Diretório de origem
origem="okul:/ess/data/satellite/goes/grb/level2/"

# Diretório de destino
destino="goes16-level2_4:/ano$ano/dia$dia_anterior/"

#Inicia o script
echo "=========================================================================================================" &>> $DIR_LOG/$ARQ_LOG
echo "=========================================================================================================" &>> $DIR_LOG/$ARQ_LOG
echo "=                                 INICIANDO SCRIPT BACKUP PARA O DRIVE LEVEL2                           =" &>> $DIR_LOG/$ARQ_LOG
echo "=========================================================================================================" &>> $DIR_LOG/$ARQ_LOG
echo "=========================================================================================================" &>> $DIR_LOG/$ARQ_LOG
echo "" &>> $DIR_LOG/$ARQ_LOG
echo "" &>> $DIR_LOG/$ARQ_LOG

# if [ ! -d "$destino" ]; then
#         echo "Diretório de destino não existe, criando..." &>> $DIR_LOG/$ARQ_LOG
#         rclone mkdir "$destino"
#         echo "Diretŕoio foi criado com sucesso!" &>> $DIR_LOG/$ARQ_LOG
# fi

# Padrão a ser buscado
padrao="*CMIPF*e$ano$dia_anterior*"

#Comando para testar linha 51 Rclone.
#--dry-run 

# Move o arquivo para o diretório de destino
rclone move $origem --include "*$padrao*" $destino --transfers=100 --dry-run --log-file=$DIR_LOG$ARQ_LOG -v ;
rclone move $origem --include "*$padrao*" $destino --transfers=100 --log-file=$DIR_LOG$ARQ_LOG -v ;
#mv "$arquivo" "$destino/"
