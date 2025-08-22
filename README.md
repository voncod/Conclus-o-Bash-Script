# Conclusao-Bash-Script
Este repositório documenta meus aprendizados sobre Bash Script durante a fase de Fundamentos Técnicos no plano de estudos DevOps + Cloud (2025).
O objetivo é consolidar conceitos básicos, comandos e exemplos práticos que servirão como referência para automações futuras.

# Estrutura básica de um script
#!/bin/bash       # Shebang: indica o interpretador
echo "Olá, mundo" # Exemplo de saída


#!/bin/bash → obrigatório no início do arquivo para indicar que será executado pelo Bash.

chmod +x script.sh → torna o script executável.

./script.sh → executa o script.

# Variáveis
nome="Luan"
echo "Meu nome é $nome"


Criadas sem espaço em volta do =.

Acessadas com $variavel.

# Entrada e Saída
read usuario
echo "Bem-vindo, $usuario"


read → captura entrada do usuário.

echo → imprime na tela.

# Condições e Controle de Fluxo
if / else / elif
if [[ $idade -ge 18 ]]; then
  echo "Maior de idade"
elif [[ $idade -gt 12 ]]; then
  echo "Adolescente"
else
  echo "Criança"
fi

case
echo "Escolha uma opção: (1/2)"
read opcao

case $opcao in
  1) echo "Você escolheu um";;
  2) echo "Você escolheu dois";;
  *) echo "Opção inválida";;
esac


;; → finaliza cada bloco de condição.

*) → funciona como "else".

# Loops
for
for i in {1..5}; do
  echo "Número $i"
done

while
contador=1
while [[ $contador -le 3 ]]; do
  echo "Contador $contador"
  ((contador++))
done

# Operadores
Comparação numérica

-eq → igual

-ne → diferente

-gt → maior que

-lt → menor que

-ge → maior ou igual

-le → menor ou igual

Comparação de strings

== → igual

!= → diferente

-z → string vazia

-n → string não vazia

Arquivos e diretórios

-e → existe

-f → é arquivo

-d → é diretório

-r → tem permissão de leitura

-w → tem permissão de escrita

-x → é executável

Lógicos

&& → E

|| → OU

# Argumentos posicionais
echo "Primeiro argumento: $1"
echo "Segundo argumento: $2"
echo "Todos argumentos: $@"


$0 → nome do script.

$1, $2 ... → argumentos passados.

$@ → todos argumentos.

# Exit codes
ls /pasta_inexistente
echo $?   # Mostra o código de saída


0 → sucesso.

Diferente de 0 → erro.

# Comandos úteis em scripts
tar – compactação
tar -czvf backup.tar.gz *.txt


tar → comando de arquivamento.

c → create (criar).

z → compress (gzip).

v → verbose (mostrar progresso).

f → file (nome do arquivo).

.gz → formato de compactação gzip.

sed – substituir texto em arquivos
sed 's/antigo/novo/g' arquivo.txt


s → substituição.

g → global (todas as ocorrências).

cron – agendamento de tarefas

Editar tarefas:

crontab -e


Exemplo: rodar backup todos os dias às 2h da manhã:

0 2 * * * /home/usuario/backup.sh

# Exemplos práticos
Backup de arquivos .txt
#!/bin/bash
data=$(date +%F)
tar -czvf backup_$data.tar.gz *.txt

Verificar se um comando existe
if command -v git &> /dev/null; then
  echo "Git está instalado"
else
  echo "Git não encontrado"
fi
