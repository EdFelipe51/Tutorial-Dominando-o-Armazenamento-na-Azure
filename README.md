# Tutorial-Dominando-o-Armazenamento-na-Azure

Tópico 1 - O que é conta de armazenamento no Azure

Uma conta de armazenamento do Azure contém todos os seus objetos de dados do Armazenamento do Azure: blobs, arquivos, filas e tabelas. Uma conta de armazenamento fornece um namespace exclusivo para os dados do Armazenamento do Microsoft Azure que podem ser acessados de qualquer lugar do mundo por HTTP ou HTTPS

Tópico 2 - Criar uma conta de armazenamento

Uma conta de armazenamento é um recurso do Azure Resource Manager. O Resource Manager é o serviço de implantação e gerenciamento do Azure. Cada recurso do Resource Manager, incluindo uma conta de armazenamento do Azure, deve pertencer a um grupo de recursos do Azure. Um grupo de recursos é um contêiner lógico para agrupar seus serviços do Azure. Quando você cria uma conta de armazenamento, tem a opção de criar um novo grupo de recursos ou usar um grupo de recursos existente.

Tópico 3 - Tipos de contas de armazenamento

O Armazenamento do Azure oferece diversos tipos de contas de armazenamento. Cada tipo é compatível com recursos diferentes e tem um modelo de preços próprio. Abaixo é descrito, os tipos de contas de armazenamento recomendados pela Microsoft para a maioria dos cenários. Todos eles usam o modelo de implantação do Azure Resource Manager.

Tipo de conta de armazenamento	

    Uso geral v2 Standard
    Blobs de blocos Premium
    Compartilhamentos de arquivos Premium
    Blobs de página Premium

Serviços de armazenamento compatíveis	

    Armazenamento de Blobs (incluindo Data Lake Storage), Armazenamento de Filas, Armazenamento de Tabelas e Arquivos do       Azure                                                                             Uso geral v2 Standard
    Armazenamento de Blobs (incluindo Data Lake Storage)                              Blobs de blocos Premium
    Arquivos do Azure                                                                 Compartilhamentos de arquivos Premium
    Blobs de páginas somente                                                          Blobs de página Premium

Opções de redundância	

   (*)RS / (**)GRS / (***)RA-GRS / (****)ZRS / (******)GZRS / (*******)RA-GZRS    Uso geral v2 Standard
     LRS / ZRS                                                                    Blobs de blocos Premium
     LRS / ZRS                                                                    Compartilhamentos de arquivos Premium         LRS / ZRS                                                                    Blobs de página Premium

Usage

 Uso geral v2 Standard
    Tipo de conta de armazenamento básico para blobs, compartilhamento de arquivos, filas e tabelas. Recomendado para a        maioria dos cenários que usam o Armazenamento do Azure. Caso deseje obter suporte para o NFS (Network File System) nos     Arquivos do Azure, use o tipo de conta de compartilhamentos de arquivos premium.

Blobs de blocos Premium
   Tipo de conta de armazenamento Premium para blobs de blocos e blobs de acréscimo. Recomendado para cenários com altas      taxas de transação ou que usam objetos menores ou exigem uma latência de armazenamento sempre baixa. 
       
Compartilhamentos de arquivos Premium
   Tipo de conta de armazenamento Premium somente para compartilhamentos de arquivos. Recomendadas para aplicações de         escala empresarial ou de alto desempenho. Use esse tipo de conta caso deseje ter uma conta de armazenamento que dê         suporte a compartilhamentos de arquivos SMB e NFS.
    
Blobs de página Premium
  Tipo de conta de armazenamento Premium somente para blobs de páginas. 


Nomenclatura:
(*) (armazenamento com redundância local)
(**) (armazenamento com redundância geográfica)
(***) (armazenamento com redundância geográfica com acesso de leitura)
(****) (armazenamento com redundância de zona)
(*****) (armazenamento com redundância de zona geográfica)
(******) (armazenamento com redundância de zona geográfica com acesso de leitura)

Obs.:

1 O Data Lake Storage é um conjunto de recursos dedicados à análise de Big Data, construído no Armazenamento de Blobs do Azure. Para obter mais informações, consulte Introdução ao Data Lake Storage e Como criar uma conta de armazenamento a ser usada com Data Lake Storage.

2 O ZRS, o GZRS e o RA-GZRS só estão disponíveis para v2 de uso geral padrão, blobs de bloco premium, compartilhamentos de arquivo premium e contas de blobs de página premium em determinadas regiões. Para mais informações, confira Redundância do Armazenamento do Microsoft Azure.

3 Contas de armazenamento de desempenho premium usam SSDs (unidades de estado sólido) para baixa latência e alta taxa de transferência.

4 Não é possível alterar uma conta de armazenamento para um tipo diferente depois que ela é criada. Para mover seus dados para uma conta de armazenamento de um tipo diferente, você precisa criar uma conta e copiar os dados para a nova conta.

Tópico 5 - Nome da conta de armazenamento
A nomear sua conta de armazenamento, lembre-se dessas regras:

1ª regra - Os nomes da conta de armazenamento devem ter entre 3 e 24 caracteres e podem conter apenas números e letras minúsculas.
2ª regra - O nome da sua conta de armazenamento deve ser exclusivo no Azure. Duas contas de armazenamento não podem ter o mesmo nome.

Tópico 6 - Pontos de extremidade padrão

Um ponto de extremidade de serviço padrão no Azure Armazenamento inclui o protocolo (HTTPS é recomendado), o nome da conta de armazenamento como o subdomínio e um domínio fixo que inclui o nome do serviço.

A tabela a seguir lista o formato para os pontos de extremidade padrão de cada um dos serviços de Armazenamento do Azure.

Serviço de armazenamento	                                  Ponto de extremidade
Armazenamento de Blobs	                                    https://<storage-account>.blob.core.windows.net
Site estático (Armazenamento de Blobs)	                    https://<storage-account>.web.core.windows.net
Data Lake Storage	                                          https://<storage-account>.dfs.core.windows.net
Arquivos do Azure	                                          https://<storage-account>.file.core.windows.net
Armazenamento de Filas	                                    https://<storage-account>.queue.core.windows.net
Armazenamento de Tabelas	                                  https://<storage-account>.table.core.windows.net

Tópico 7 - Parâmetros para conta de armazenamento

Quando você cria uma conta de armazenamento, o tipo de conta de armazenamento é especificado pelo parâmetro kind (por exemplo, StorageV2). O nível de desempenho e a configuração de redundância são especificados juntos pelo parâmetro sku ou SkuName (por exemplo, Standard_GRS). Abaixo segue os valores a serem utilizados para o parâmetro kind e o parâmetro sku ou SkuName para criar um tipo específico de conta de armazenamento com a configuração de redundância desejada.

Tipo de conta de armazenamento	

    Uso geral v2 Standard
    Blobs de blocos Premium
    Compartilhamentos de arquivos Premium
    Blobs de página Premium
    Uso geral v1 Standard herdado
    Armazenamento de blobs herdado

Configurações de redundância com suporte	

    LRS / GRS / RA-GRS / ZRS / GZRS / RA-GZRS     (Uso geral v2 Standard)
    LRS / ZRS                                     (Blobs de blocos Premium)
    LRS / ZRS                                     (Compartilhamentos de arquivos Premium)
    LRS                                           (Blobs de página Premium)
    LRS/GRS/RA-GRS                                (so geral v1 Standard herdado)
    LRS/GRS/RA-GRS                                (Armazenamento de blobs herdado)

Valores com suporte para o parâmetro Variante

    StorageV2                                     (Uso geral v2 Standard)
    BlockBlobStorage                              (Blobs de blocos Premium)
    Compartilhamentos de arquivos Premium         (Compartilhamentos de arquivos Premium)
    Blobs de página Premium                       (Blobs de página Premium)
    Uso geral v1 Standard herdado                 (so geral v1 Standard herdado)                                     
    Armazenamento de blobs herdado                (Armazenamento de blobs herdado)
     

Valores suportados para o parâmetro SKU ou SkuName	

    Standard_LRS/Standard_GRS/Standard_RAGRS/Standard_ZRS/Standard_GZRS/Standard_RAGZRS (Uso geral v2 Standard)
    Premium_LRS / Premium_ZRS                                                           (Blobs de blocos Premium)
    Premium_LRS / Premium_ZRS                                                           (Compartilhamentos de arquivos                                                                                               Premium)
    Premium_LRS                                                                         (Blobs de página Premium)
    Standard_LRS / Standard_GRS / Standard_RAGRS                                        (so geral v1 Standard herdado)
    Standard_LRS / Standard_GRS / Standard_RAGRS                                        (Armazenamento de blobs herdado)
    
Oferece suporte ao namespace hierárquico

    Uso geral v2 Standard                        OFERECE SUPORTE SIM
    Blobs de blocos Premium                      OFERECE SUPORTE SIM
    Compartilhamentos de arquivos Premium        OFERECE SUPORTE NÃO
    Blobs de página Premium                      OFERECE SUPORTE NÃO
    Uso geral v1 Standard herdado                OFERECE SUPORTE NÃO
    Armazenamento de blobs herdado               OFERECE SUPORTE NÃO


Tópico 8 - Criar tokens SAS para contêineres de armazenamento

criar tokens SAS (Assinatura de Acesso Compartilhado) de delegação de usuário usando o portal do Azure ou o Gerenciador de Armazenamento do Azure. Os tokens SAS de delegação de usuário são protegidos com credenciais do Microsoft Entra. Um token SAS oferece acesso seguro e delegado aos recursos da conta de armazenamento do Azure.

1=[https://my.blob.core.windows.net/source-en/source-english.docx] 2=[?] 3=[sv=2019-12-12&st=2021-01-26T18%3A30%3A20Z&se=2021-02-05T18%3A30%3A00Z&sr=c&sp=rl&sig=d7PZKyQsIeE6xb%2B1M4Yb56I%2FEEKoNIF65D%2Fs0IFsYcE%3D]

1 = Storage resource URL (URL Grupo de Armazenamento)
2 = Delimeter Character  (Delimititador de caracter)
3 = SAS Token            (token criptografado SAS)

Em linhas gerais, veja como os tokens SAS funcionam:

1º Seu aplicativo envia o token SAS para o Armazenamento do Microsoft Azure como parte de uma solicitação da API REST.

2º Em seguida, se o serviço de armazenamento verificar que o SAS é válido, a solicitação será autorizada. Se o token SAS for considerado inválido, a solicitação será recusada e o código de erro 403 (Proibido) será retornado.

O Armazenamento de Blobs do Azure oferece três tipos de recursos:

    As contas de armazenamento fornecem um namespace exclusivo no Azure para os dados.
    Os contêineres de armazenamento de dados estão localizados em contas de armazenamento e organizam conjuntos de blobs.
    Os blobs estão localizados em contêineres e armazenam dados binários e de texto, como arquivos, texto e imagens.

Tópico 9 - Quando usar um token SAS

Treinamento de modelos personalizados. O conjunto de documentos de treinamento montado precisa ser carregado em um contêiner de Armazenamento de Blobs do Azure. Você pode usar um token SAS para permitir acesso aos documentos de treinamento.

Uso de contêineres de armazenamento com acesso público. Você pode usar um token SAS para permitir acesso limitado aos recursos de armazenamento que têm acesso de leitura público.

Obs.:

1º Se a conta de armazenamento do Azure estiver protegida por uma rede virtual ou um firewall, você não poderá permitir acesso usando um token SAS. Você precisará usar uma identidade gerenciada para conceder acesso ao recurso de armazenamento.

2º A Identidade gerenciada oferece suporte a contas de Armazenamento de Blobs do Azure acessíveis de maneira pública ou privada.

3º Os tokens SAS concedem permissões aos recursos de armazenamento e devem ser protegidos da mesma forma que uma chave de conta.

4º As operações que usam tokens SAS só devem ser executadas em uma conexão HTTPS e os URIs SAS só devem ser distribuídos em uma conexão segura, como HTTPS.


                                    

