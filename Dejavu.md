# DataRecoveryCyberCrimes
Este estudo foca na recuperação de arquivos formatados, investigando a eficácia das ferramentas Foremost, Scalpel e Magic Rescue,Deca,Dejavu Forensics no ambiente Linux.
No Windows, são investigadas as ferramentas Autopsy, Recuva e Photorec. 

Dejavu: Ferramenta autoral

A ferramenta desenvolvida pelo autor adota uma abordagem de aprendizado de máquina
para reconhecer padrões de cluster em arquivos JPEG,PNG especificamente utilizando Máquina de
Vetores de Suporte (SVM - Support Vector Machine). Na fase de extração de características,
a ferramenta gera um histograma do cluster em análise. Posteriormente, durante a etapa de
classificação, este histograma serve como um conjunto de atributos de entrada para o modelo de
aprendizado estatístico. Para a implementação desta ferramenta, foram utilizadas as seguintes
bibliotecas de software:
• libtsk-dev (sleuthkit): Este pacote é responsável pela leitura dos clusters do dispositivo
de armazenamento de destino. Facilita a extração dos dados necessários para análise
subsequente.
• libmagic-dev: Esta biblioteca é usada para realizar o Data Carving, um processo que
envolve a busca por tipos específicos de arquivos baseado em suas assinaturas digitais
(números mágicos).
• liblinear-dev: Essa biblioteca desempenha uma função crucial na etapa de reconhecimento de padrões, utilizando um algoritmo de discriminante linear para classificar os
dados.
• libsvm-dev: Essa biblioteca é usada na etapa de reconhecimento de padrões, aplicando
a metodologia da Máquina de Vetores de Suporte (Support Vector Machine - SVM) para
classificar os dados.

-vv: abreviação de verbose para imprimir na tela o progresso da especialização.
• -o: abreviação de output, para o caminho de destino dos arquivos a serem recuperados
(em outra partição, como um dispositivo de memória auxiliar). É necessário que a pasta
seja criada antes que a ferramenta de criação seja chamada.
• Não há sinalizador (diretriz) para a partição de origem, basta citá-la no comando.
• –dejavu: com aprendizado de máquina adicionado ao Data Carving.
• -oneclass: Especifica que a análise será conduzida em um único modo, ou seja, uma classe de arquivo.
• -fex "raw": Indica que o método de extração de características utilizado é o "raw", que provavelmente se refere a uma extração direta dos dados brutos dos arquivos.
• /dev/sdb1: Especifica o dispositivo ou partição a ser analisado, neste caso, "/dev/sdb1".
• Exemplo:./dejavu -vv -o /home/kali/Desktop/Dejavu/out -oneclass -fex "raw" /dev/sdb1

•Similar ao comando anterior, mas com -fex "histo", sugerindo que a extração de características agora é baseada na criação e análise de histogramas dos arquivos.
•./dejavu -vv -o /home/kali/Desktop/Dejavu/out -oneclass -nofooter -fex "raw" /dev/sdb1

•Similar ao primeiro comando, porém com -nofooter, indicando que não será incluído um rodapé nos resultados da análise.
•./dejavu -vv -o /home/kali/Desktop/Dejavu/out -oneclass -nofooter -fex "histo" /dev/sdb1

•Similar ao segundo comando, mas também com -nofooter.
•Esses comandos ilustram diferentes configurações e opções usadas na ferramenta DejaVu para realizar análises de recuperação de dados. O uso de -fex "raw" indica que a extração direta de dados brutos dos arquivos está sendo realizada, enquanto -fex "histo" sugere a extração baseada em histogramas. A opção -nofooter controla a inclusão ou exclusão do rodapé nos resultados.
• Esses comandos ilustram diferentes configurações e abordagens para a análise de recuperação de arquivos PNG-JPEG usando a ferramenta DejaVu.

• No console, usamos Uma abordagens para a análise de recuperação de arquivos PNG.

Make
./dejavu -vv -o /home/kali/Desktop/Dejavu/out -oneclass -fex "raw" /dev/sdb1
./dejavu -vv -o /home/kali/Desktop/Dejavu/out -oneclass -fex "histo" /dev/sdb1
./dejavu -vv -o /home/kali/Desktop/Dejavu/out -oneclass -nofooter -fex "raw" /dev/sdb1
./dejavu -vv -o /home/kali/Desktop/Dejavu/out -oneclass -nofooter -fex "histo" /dev/sdb1 

• No console, usamos Uma abordagens para a análise de recuperação de arquivos JPEG.

Make
./dejavu -vv -o /home/kali/Desktop/Dejavu/out -oneclass -fex "raw" /dev/sdb1
./dejavu -vv -o /home/kali/Desktop/Dejavu/out -oneclass -fex "histo" /dev/sdb1
