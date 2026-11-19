# Atalhos do Windows no Mac

Atalhos com Control para macOS usando o Karabiner-Elements. A configuração inclui navegação, seleção de texto, copiar, recortar e colar, além da personalização Ctrl+Y para apagar a linha atual.

## Atalhos

| Teclas | Ação |
|---|---|
| Ctrl+X | Recortar |
| Ctrl+C | Copiar |
| Ctrl+V | Colar |
| Ctrl+A | Selecionar tudo |
| Ctrl+Z | Desfazer |
| Ctrl+← | Mover uma palavra à esquerda |
| Ctrl+→ | Mover uma palavra à direita |
| Ctrl+Shift+← | Selecionar uma palavra à esquerda |
| Ctrl+Shift+→ | Selecionar uma palavra à direita |
| Home | Início da linha |
| End | Fim da linha |
| Ctrl+Home | Início do documento |
| Ctrl+End | Fim do documento |
| Shift+End | Selecionar até o fim da linha |
| Ctrl+Shift+End | Selecionar até o fim do documento |
| Ctrl+Shift+Home | Selecionar até o início do documento |
| Ctrl+Y | Apagar a linha atual |

## Instalação

1. Instale o [Karabiner-Elements pelo site oficial](https://karabiner-elements.pqrs.org/).
2. Conclua as etapas indicadas em Setup para serviços em segundo plano, Acessibilidade e extensão do teclado virtual.
3. Selecione o perfil desejado e abra Complex Modifications → Add your own rule.
4. Cole o conteúdo de `atalhos-windows-karabiner.json` e salve.
5. Se já houver uma regra com esse nome, edite essa regra para atualizar seu conteúdo.
6. Teste os atalhos em um documento temporário.

O arquivo contém uma regra individual. Ao aplicá-lo, incorpore a regra ao perfil existente e preserve as outras configurações. Crie uma cópia de segurança de `~/.config/karabiner/karabiner.json` antes de editar esse arquivo.

## Comportamento e verificação

Control e Shift aceitam as teclas de ambos os lados. Os remapeamentos estão limitados às combinações da tabela.

Ctrl+Y executa Command+←, Command+Shift+→, Shift+→ e Backspace para selecionar e apagar a linha e a quebra seguinte, quando houver. A navegação por linha depende do aplicativo e pode considerar linhas visuais em textos com quebra automática. O comportamento em aplicativos ainda precisa de validação prática.

Para validar o JSON e detectar entradas duplicadas, execute na pasta do projeto

```sh
ruby -rjson -e 'r = JSON.parse(File.read("atalhos-windows-karabiner.json")); m = r.fetch("manipulators"); abort "Entradas duplicadas" unless m.map { |x| x.fetch("from") }.uniq.size == m.size; puts "#{m.size} atalhos válidos"'
```

## Manutenção

Edite a regra versionada, valide e aplique o conteúdo atualizado no Karabiner. Registre as alterações em commits Git. Para desativar os remapeamentos, desabilite ou remova a regra em Complex Modifications.
