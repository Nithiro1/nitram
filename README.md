<p align="center">
  <img src="assets/nitram-icon.svg" width="96" height="96" alt="Ícone do NitRAM">
</p>

<h1 align="center">NitRAM</h1>

<p align="center">
  Disco na memória RAM, gratuito e de código aberto, feito para deixar menos rastros.<br>
  Um app <b>Nithiro</b>.
</p>

> **Status:** em desenvolvimento. A interface e o wireframe estão prontos; o app em Rust está começando. Ainda não há versão para baixar.

## Download

Ainda não há versão para baixar. Quando o NitRAM estiver pronto, o instalador vai aparecer na página de [Releases](../../releases). Para ser avisado, clique em **Watch → Custom → Releases** no topo desta página.

## O que é

O NitRAM cria uma unidade de disco (por exemplo `R:`) que existe só na memória RAM. Tudo o que você grava ali é muito rápido e some quando o disco é desmontado ou o computador desliga.

O foco do NitRAM é **privacidade**: além de criar o disco, ele mostra onde o Windows ainda pode guardar cópias fora da RAM e ajuda a fechar essas brechas.

## Recursos planejados

- Criar discos na RAM com tamanho, letra e nome à escolha
- **Memória travada**: o conteúdo não vai para o `pagefile.sys`
- **Apagamento seguro**: a memória é sobrescrita com zeros ao desmontar, desligar ou hibernar
- **Botão de pânico**: um atalho de teclado apaga todos os discos na hora
- Apagar ao bloquear o Windows ou após um tempo sem uso
- **Verificação de privacidade**: paginação, hibernação, despejo de memória, indexação e arquivos recentes
- Salvar imagem criptografada ao desligar (opcional e desligado por padrão)
- Fica recolhido num **ponto pulsante** na tela; um clique abre o app

## Privacidade: o que o NitRAM protege e o que não protege

Um RAM disk deixa muito menos rastros que um disco comum, mas não deixa "zero rastros" sozinho. O NitRAM é transparente sobre isso.

| Risco | O NitRAM ajuda? |
|---|---|
| Windows mover memória para o `pagefile.sys` | ✅ Trava a memória e verifica se a paginação está criptografada |
| Hibernação gravar a RAM no `hiberfil.sys` | ✅ Avisa e oferece desativar; apaga os discos antes de hibernar |
| Despejo de memória numa tela azul (`MEMORY.DMP`) | ⚠️ Avisa e sugere desativar o despejo completo |
| Outros programas guardarem nomes de arquivos, miniaturas e índices | ⚠️ Parcial: bloqueia a indexação e limpa arquivos recentes |
| Dados restantes na RAM logo após desligar | ✅ Sobrescreve a memória com zeros |
| Vírus ou invasor com o computador ligado e o disco montado | ❌ Não protege. Com o disco montado, os arquivos ficam acessíveis como em qualquer outro disco |

## Como vai funcionar

O NitRAM não tem um driver de kernel próprio. Ele usa o [WinFsp](https://github.com/winfsp/winfsp), que já traz um driver assinado:

```
Programa grava em R:\  →  Windows  →  driver do WinFsp  →  NitRAM  →  memória RAM
```

O app está sendo escrito em **Rust**.

## Contribuir

Ideias e relatos de problemas são bem-vindos. Leia o [guia de contribuição](CONTRIBUTING.md) e o [código de conduta](CODE_OF_CONDUCT.md).

Encontrou uma falha de segurança? Não abra uma issue pública: siga a [política de segurança](SECURITY.md).

## Licença

O NitRAM é software livre, distribuído sob a **GNU General Public License versão 3 ou posterior** (GPL-3.0-or-later). Veja o arquivo [LICENSE](LICENSE).

O WinFsp é de Bill Zissimopoulos e usa a licença GPLv3 com exceção para software livre.

---

### English

NitRAM is a free and open-source RAM disk for Windows, focused on leaving fewer traces: locked memory, secure wipe, a panic hotkey and a privacy check-up for the places where Windows can still copy data to disk. It is being built in Rust on top of WinFsp and licensed under GPL-3.0-or-later. No release is available yet.
