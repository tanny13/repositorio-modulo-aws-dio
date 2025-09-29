## AWS CloudFormation
* O AWS CloudFormation é o serviço da AWS usado para provisionar e gerenciar infraestrutura como código (IaC). Em vez de criar recursos manualmente no console, você descreve tudo em templates (YAML ou JSON), e o CloudFormation cuida de criar, configurar e atualizar automaticamente.
* Infraestrutura como código: descreve recursos como EC2, S3, RDS, VPC etc. em arquivos versionáveis.
* Automação: cria e atualiza ambientes inteiros com um único comando.
* Padrões reutilizáveis: você pode usar os mesmos templates para replicar ambientes (ex.: dev, teste, produção).
* Gerenciamento de dependências: ele entende a ordem de criação (ex.: cria a VPC antes das instâncias EC2).
* Stacks: os recursos são organizados em pilhas (stacks), fáceis de criar, atualizar e excluir.
* Rollback automático: se algo falhar, ele reverte para o estado anterior.
![imagem esquema AWS ClouFormation](images/AWS-CloudFormation.png)

### Exemplo de template que cria um bucket S3 com versionamento habilitado.
```yaml
AWSTemplateFormatVersion: "2010-09-09"

Description: Exemplo simples de CloudFormation - Criando um bucket S3

Resources:
  MeuBucketS3:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: meu-bucket-exemplo-cloudformation
      VersioningConfiguration:
        Status: Enabled

Outputs:
  BucketNameOutput:
    Description: Nome do bucket criado
    Value: !Ref MeuBucketS3`
```
### Explicação
* AWSTemplateFormatVersion: versão da linguagem do CloudFormation.
* Description: texto explicativo.
* Resources: parte principal, onde se define os recursos.
  * Onde é criado MeuBucketS3, do tipo AWS::S3::Bucket.
  * Configuração do versionamento como ativo.
* Outputs: mostra informações de saída depois da criação (nesse caso, o nome do bucket).
