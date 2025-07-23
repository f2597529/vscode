# vscode
java extension for code


Para compactar uma pasta no terminal Linux e dividi-la em partes de 20 MB cada, você pode usar o comando zip em conjunto com o comando split.

Compactando e dividindo em partes

    Navegue até o diretório onde a pasta que você quer compactar está localizada:
    Bash

cd /caminho/para/sua/pasta/pai

Substitua /caminho/para/sua/pasta/pai pelo caminho real do diretório que contém a pasta que você deseja compactar.

Use o comando zip e split para compactar a pasta e dividi-la:
Bash

    zip -r -s 20m nome_do_arquivo_zip.zip nome_da_sua_pasta/

    Vamos entender o que cada parte do comando faz:

        zip: É o comando para compactar arquivos e pastas.

        -r: Significa "recursivo", ou seja, inclui todos os subdiretórios e arquivos dentro da pasta.

        -s 20m: Essa é a chave! Define o tamanho máximo de cada parte compactada em 20 megabytes (m para megabytes).

        nome_do_arquivo_zip.zip: É o nome que você quer dar ao arquivo ZIP principal. O zip irá adicionar sufixos como .zip.001, .zip.002, etc., para cada parte.

        nome_da_sua_pasta/: É o nome da pasta que você deseja compactar. Não esqueça da barra (/) no final se for uma pasta.

Exemplo prático

Se você tem uma pasta chamada meus_documentos e quer compactá-la em arquivos de 20 MB com o nome base documentos_backup.zip, o comando seria:
Bash

zip -r -s 20m documentos_backup.zip meus_documentos/

Após a execução, você encontrará vários arquivos no seu diretório atual, como:

    documentos_backup.zip.001

    documentos_backup.zip.002

    documentos_backup.zip.003

    E assim por diante, cada um com aproximadamente 20 MB (o último pode ser menor).

Para descompactar as partes

Para descompactar esses arquivos novamente, você precisará ter todas as partes no mesmo diretório e usar o comando zip com a opção -F para "fixar" (reunir) as partes, e depois o comando unzip ou zip -F novamente:

    Reúna as partes (opcional, mas recomendado para clareza):
    Bash

zip -F documentos_backup.zip --out documentos_completos.zip

Este comando irá juntar todas as partes em um único arquivo documentos_completos.zip.

Descompacte o arquivo completo:
Bash

unzip documentos_completos.zip

Ou, se preferir descompactar diretamente das partes sem juntar primeiro:
Bash

    zip -F documentos_backup.zip --out - | funzip

    Este comando funzip é um utilitário que pode ser usado para extrair o conteúdo de um arquivo ZIP lido da entrada padrão, ou seja, diretamente do "pipe" do zip -F.

Se tiver alguma dúvida ou precisar de mais ajuda, é só perguntar!
