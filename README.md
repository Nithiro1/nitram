<p align="center">
  <img src="assets/nitram-icon.svg" width="96" height="96" alt="Ícone do NitRAM">
</p>

<h1 align="center">NitRAM</h1>

<p align="center">
  Disco na memória RAM, gratuito e de código aberto, feito para deixar menos rastros.<br>
  Um app <b>Nithiro</b>.
</p>

## Download

Baixe a versão mais nova na página de **[Releases](../../releases/latest)**:

- `NitRAM-<versão>-instalador.exe`: instala só para você, sem pedir administrador.
- `NitRAM-<versão>-portatil.zip`: descompacte e abra o `nitram.exe`.

Precisa de **Windows 10 ou 11 de 64 bits** e do **[WinFsp](https://winfsp.dev/rel/)** (gratuito). Se o WinFsp faltar, o instalador avisa e abre a página dele.

O NitRAM ainda não tem assinatura digital, então o Windows pode mostrar "O Windows protegeu o computador". Clique em **Mais informações → Executar assim mesmo**. Para conferir que o arquivo é o original, compare a impressão digital com o `SHA256SUMS.txt` da mesma página:

```
Get-FileHash .\NitRAM-1.0.0-instalador.exe
```

## O que é

O NitRAM cria uma unidade de disco (por exemplo `R:`) que existe só na memória RAM. Tudo o que você grava ali é muito rápido e some quando o disco é desmontado ou o computador desliga.

O foco do NitRAM é **privacidade**: além de criar o disco, ele mostra onde o Windows ainda pode guardar cópias fora da RAM e ajuda a fechar essas brechas.

## Recursos

- Discos na RAM com tamanho, letra e nome à escolha
- **Memória travada**: o conteúdo não vai para o `pagefile.sys`
- **Apagamento seguro**: a memória é sobrescrita com zeros ao desmontar, fechar o NitRAM ou desligar o Windows
- **Botão de pânico**: um atalho de teclado apaga todos os discos na hora, em qualquer programa
- Apagar ao bloquear o Windows (Win + L) ou após um tempo sem uso
- **Fora da indexação**: a Pesquisa do Windows não copia o conteúdo para o índice
- **Pasta TEMP na RAM**: arquivos temporários dos programas ficam no disco enquanto ele existe
- **Montar ao iniciar**: o disco é recriado vazio sempre que o NitRAM abre
- **Imagem criptografada** (opcional): salva o conteúdo no HD com Argon2id e XChaCha20-Poly1305 e restaura com a senha
- **Verificação de privacidade**: paginação, hibernação, inicialização rápida, despejo de memória, permissão para travar memória e arquivos recentes, com correção em um clique
- Fica recolhido num **ponto pulsante** na tela; um clique abre o app

## Privacidade: o que o NitRAM protege e o que não protege

Um RAM disk deixa muito menos rastros que um disco comum, mas não deixa "zero rastros" sozinho. O NitRAM é transparente sobre isso.

| Risco | O NitRAM ajuda? |
|---|---|
| Windows mover memória para o `pagefile.sys` | ✅ Trava a memória e verifica se a paginação está criptografada |
| Hibernação gravar a RAM no `hiberfil.sys` | ⚠️ Avisa e oferece desativar a hibernação e a inicialização rápida |
| Despejo de memória numa tela azul (`MEMORY.DMP`) | ⚠️ Avisa e oferece desativar o despejo completo |
| Pesquisa do Windows indexar o conteúdo | ✅ Os arquivos do disco ficam fora da indexação |
| Atalhos de arquivos recentes apontando para o disco | ✅ Apaga ao desmontar (se ligado na Privacidade) |
| Miniaturas de imagens e outros rastros de programas | ❌ Não protege. O Explorador e outros programas podem guardar cópias próprias |
| Dados restantes na RAM depois de desmontar | ✅ Sobrescreve a memória com zeros |
| Vírus ou invasor com o computador ligado e o disco montado | ❌ Não protege. Com o disco montado, os arquivos ficam acessíveis como em qualquer outro disco |

## Como funciona

O NitRAM não tem um driver de kernel próprio. Ele usa o [WinFsp](https://github.com/winfsp/winfsp), que já traz um driver assinado:

```
Programa grava em R:\  →  Windows  →  driver do WinFsp  →  NitRAM  →  memória RAM
```

O app é escrito em **Rust**, com a interface em **[Slint](https://slint.dev)** (sem navegador embutido).

## Código-fonte

O código-fonte de cada versão está na página da versão em [Releases](../../releases), no arquivo `NitRAM-<versão>-codigo-fonte.zip`. As instruções para compilar estão no `README.md` de dentro dele.

## Contribuir

Ideias e relatos de problemas são bem-vindos. Leia o [guia de contribuição](CONTRIBUTING.md) e o [código de conduta](CODE_OF_CONDUCT.md).

Encontrou uma falha de segurança? Não abra uma issue pública: siga a [política de segurança](SECURITY.md).

## Licença

O NitRAM é software livre, distribuído sob a **GNU General Public License versão 3 ou posterior** (GPL-3.0-or-later). Veja o arquivo [LICENSE](LICENSE).

Usa o WinFsp, de Bill Zissimopoulos (GPLv3 com exceção para software livre), o Slint (GPLv3) e as fontes Lexend e IBM Plex Mono (SIL Open Font License).

---

### English

NitRAM is a free and open-source RAM disk for Windows, focused on leaving fewer traces: locked memory, secure wipe, a global panic hotkey, wipe on lock or inactivity, indexing opt-out, a RAM-backed TEMP folder, optional encrypted images (Argon2id + XChaCha20-Poly1305) and a privacy check-up for the places where Windows can still copy data to disk. It is built in Rust and Slint on top of WinFsp and licensed under GPL-3.0-or-later. Downloads and the source code of each version are on the Releases page.
