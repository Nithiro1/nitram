# Política de segurança

O NitRAM lida com dados que as pessoas querem manter privados, então falhas de segurança são levadas a sério.

## Como relatar uma falha

**Não abra uma issue pública.** Use o relato privado do GitHub:

1. Abra a aba **Security** deste repositório.
2. Clique em **Report a vulnerability**.
3. Descreva a falha, como reproduzir e o impacto.

Você vai receber uma resposta assim que possível. Depois de corrigida, a falha é divulgada com crédito a quem relatou, se a pessoa quiser.

## O que conta como falha de segurança

- Dados de um disco do NitRAM indo parar no disco rígido sem o usuário ter pedido (por exemplo, no `pagefile.sys`, em arquivos temporários ou em logs).
- Memória que não é zerada ao desmontar, quando o apagamento seguro está ligado.
- Imagem salva que pode ser aberta sem a senha.
- Botão de pânico ou apagamento automático que deixa algum disco para trás.
- Qualquer forma de outro usuário do computador acessar um disco que não é dele.

## O que o NitRAM não promete

Com o disco montado, qualquer programa com acesso ao sistema consegue ler os arquivos, como em qualquer outro disco. Isso é uma limitação conhecida, não uma falha. A lista completa do que o NitRAM protege e não protege está no [README](README.md#privacidade-o-que-o-nitram-protege-e-o-que-não-protege).

## Versões com suporte

O NitRAM ainda não tem versões publicadas. Quando tiver, só a versão mais recente receberá correções de segurança.
