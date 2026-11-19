# Configuração automática dos atalhos do Windows no macOS

Português (Brasil) · [English](SETUP-WITH-AI.en.md)

Entregue este arquivo a uma IA com acesso ao terminal, à internet e à interface gráfica do Mac de destino e peça que execute as instruções. O resultado esperado é a regra do repositório instalada, ativa e verificada.

## Instrução para a IA executora

Execute este procedimento de ponta a ponta neste Mac. Tome as decisões técnicas necessárias, use as ferramentas disponíveis e prossiga com as etapas autorizadas sem pedir confirmações rotineiras. O pedido de execução deste documento autoriza baixar o repositório e instalar o Karabiner-Elements de sua fonte oficial, incorporar a regra ao perfil ativo e criar cópias de segurança.

A autenticação administrativa e determinadas permissões protegidas pelo macOS podem exigir ação humana. Em um Mac já provisionado com as permissões necessárias, execute todo o fluxo automaticamente. Se o sistema exigir interação pessoal, prepare a tela exata, informe a ação mínima necessária e retome o fluxo após sua conclusão. Use as permissões disponíveis conforme as políticas da ferramenta que estiver executando este documento.

## 1. Inspecionar o Mac

1. Confirme que o sistema é macOS e identifique versão, arquitetura e usuário da sessão gráfica.
2. Localize o Karabiner-Elements, verifique a versão instalada e examine sua aba Setup e seus registros.
3. Identifique o diretório de configuração efetivamente usado pelo aplicativo. O padrão é `~/.config/karabiner/karabiner.json`. Considere XDG_CONFIG_HOME, links simbólicos e configurações existentes.
4. Identifique o perfil selecionado, as regras existentes e eventuais conflitos com remapeamentos de Control, Command, Home, End e setas.
5. Preserve configurações de teclado, layout, dispositivos e perfis existentes. Registre qualquer conflito que impeça os atalhos solicitados de funcionar e resolva apenas o necessário dentro deste escopo.

## 2. Obter a configuração

Use o repositório público

`https://github.com/leonardo-santos-trix/windows-shortcuts-for-mac`

Se já houver uma cópia local, confira seu remoto e estado antes de usá-la. Caso contrário, clone em uma pasta de projetos acessível ao usuário. Se Git estiver indisponível, baixe o arquivo da branch main pelo GitHub sem instalar ferramentas de desenvolvimento apenas para fazer o download.

O arquivo de entrada é `atalhos-windows-karabiner.json` na raiz do repositório. Leia também AGENTS.md e README.md. Registre o commit ou a versão obtida.

Valide o JSON, a presença de description e manipulators, os tipos das regras e a ausência de entradas from duplicadas. Use a versão atual do arquivo como fonte dos atalhos. Este procedimento foi preparado quando a configuração continha 22 combinações.

## 3. Instalar e preparar o Karabiner

Se já estiver instalado e compatível, utilize a instalação existente. Caso precise instalar, obtenha a versão compatível com o macOS pelo site oficial. Use Homebrew se já estiver disponível ou baixe o instalador oficial, confira sua assinatura e conclua a instalação.

Abra o aplicativo na sessão gráfica do usuário e conclua as etapas apresentadas em Setup. Verifique os serviços em segundo plano, a Acessibilidade, a captura de eventos e a extensão do teclado virtual conforme a versão instalada.

Configure o tipo de teclado virtual conforme o teclado em uso. Confirme que o dispositivo pretendido está habilitado para modificações. Reabra ou reinicie os componentes do Karabiner quando o próprio aplicativo indicar essa necessidade.

Em equipamentos gerenciados, utilize o provisionamento autorizado já existente. Senha, Touch ID, aprovação protegida ou reinicialização exigida pelo macOS devem ser tratados pela interface oficial. Quando uma dessas etapas impedir a continuação automática, registre o ponto de retomada e prossiga com o trabalho independente disponível.

## 4. Aplicar a regra automaticamente

Prefira incorporar o JSON diretamente à configuração efetiva quando houver acesso de escrita.

1. Feche o editor de regras do Karabiner para evitar gravações concorrentes. Se o arquivo ainda não existir, inicialize o aplicativo para gerar seu perfil padrão.
2. Leia a configuração completa e localize exatamente o perfil selecionado. Se o estado for ambíguo, use a interface do Karabiner para identificar ou selecionar o perfil pretendido antes de gravar.
3. Crie uma cópia integral de segurança com data e hora, preservando os atributos do arquivo.
4. No array complex_modifications.rules do perfil selecionado, substitua a regra cuja description corresponda à regra baixada. Se ela ainda não existir, adicione-a. Inicialize os campos de modificações complexas ausentes.
5. Preserve os demais campos. Mantenha a ordem interna dos manipulators da regra baixada. Elimine apenas duplicatas da própria regra gerenciadas por este procedimento.
6. Faça a alteração de forma idempotente. Uma segunda execução com o mesmo arquivo deve produzir o mesmo estado e apenas uma cópia ativa da regra.
7. Antes de gravar, confirme que o arquivo original continua igual à versão lida. Se tiver mudado, releia e refaça a incorporação.
8. Grave em arquivo temporário no mesmo diretório, valide-o e substitua o destino atomicamente. Preserve o proprietário, as permissões e o destino real de links simbólicos.
9. Releia o arquivo resultante e confirme a igualdade entre a regra instalada e a regra baixada, além da preservação das demais configurações.

Se a ferramenta permitir apenas interação gráfica, abra Complex Modifications → Add your own rule, cole o conteúdo do arquivo e salve. Para uma regra já existente, edite-a. Depois confirme seu conteúdo e sua presença no perfil ativo.

## 5. Verificar o funcionamento

Confirme que o aplicativo recarregou a configuração, que a regra está ativa e que os registros estão livres de erros relacionados à nova regra. Use Setup, Log e EventViewer para diagnosticar serviços, driver, dispositivos e eventos.

Crie um documento temporário com várias palavras, três parágrafos, uma linha vazia e um parágrafo longo com quebra visual. Execute os testes exclusivamente nesse documento e confira a posição do cursor, o intervalo selecionado e o conteúdo resultante.

| Combinação | Resultado esperado |
|---|---|
| Ctrl+X / C / V | Recortar, copiar e colar |
| Ctrl+A | Selecionar tudo |
| Ctrl+← / → | Mover por palavra |
| Ctrl+Shift+← / → | Ampliar ou reduzir a seleção por palavra |
| Ctrl+Shift+↑ / ↓ | Selecionar até o limite do parágrafo |
| Home / End | Ir ao início ou fim da linha |
| Ctrl+Home / End | Ir ao início ou fim do documento |
| Shift+End | Selecionar até o fim da linha |
| Ctrl+Shift+Home / End | Selecionar até o início ou fim do documento |
| Ctrl+Backspace / Delete | Apagar a palavra à esquerda ou à direita |
| Ctrl+Z / Ctrl+Shift+Z | Desfazer ou refazer |
| Ctrl+Y | Apagar a linha atual |

Teste seleção nas duas direções para verificar sua ampliação e redução. Teste exclusão no início, meio e fim do documento. Confira Control e Shift dos dois lados quando o ambiente permitir.

Os limites de palavra e parágrafo seguem o editor. Ctrl+Y usa uma sequência de navegação e exclusão e precisa ser avaliado também em linhas vazias, na última linha e com quebra visual.

Verifique se os eventos sintetizados pela automação realmente atravessam o Karabiner usando EventViewer ou evidência equivalente. Ferramentas que injetam eventos após o remapeamento podem testar somente o comando final. Registre o alcance real de cada teste. Uma configuração válida em JSON, isoladamente, é insuficiente para declarar que os testes de teclado passaram.

Se um teste falhar, diagnostique permissões, estado dos serviços, dispositivo habilitado, conflitos e percurso dos eventos. Corrija falhas recuperáveis e repita os casos afetados. Preserve o texto de trabalho do usuário e descarte somente o documento temporário criado para os testes.

## 6. Finalizar e permitir recuperação

Conclua com um relatório curto contendo a versão do Karabiner, o perfil atualizado, a origem da regra, a localização da cópia de segurança e os testes efetivamente realizados. Informe qualquer etapa bloqueada e a ação concreta exigida para retomá-la. Declare conclusão funcional somente após evidência dos atalhos em funcionamento.

Se a aplicação da regra causar erro de configuração, restaure a cópia de segurança e confirme a recuperação antes de tentar novamente.

## Referências oficiais

- [Repositório e configuração](https://github.com/leonardo-santos-trix/windows-shortcuts-for-mac)
- [Instalação do Karabiner-Elements](https://karabiner-elements.pqrs.org/docs/getting-started/installation/)
- [Configurações exigidas pelo macOS](https://karabiner-elements.pqrs.org/docs/manual/misc/required-macos-settings/)
- [Localização da configuração](https://karabiner-elements.pqrs.org/docs/manual/misc/configuration-file-path/)
