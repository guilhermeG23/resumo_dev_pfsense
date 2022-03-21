### Resumo do guia estilo desenvolvedor
___
#### Link da página original:
* https://docs.netgate.com/pfsense/en/latest/references/developer-style-guide.html
___
#### Como o PF fazia
* Tudo em um unico arquivo PHP -> Página e suas funções;
* Uso de variaveis globais como forma de compartilhamento em todos os arquivos;
___

#### PF Atual
* Páginas adotam o modelo MVC
* O arquivo que irá fornecer a interface só deve ter as partes necessárias a isso
* Se essa página tiver funcionabilidades, essas devem ser providas por demais arquivos que devem ser requisitados dentro de ```/usr/local/pfsense/include/www```, de preferencia por colocar suas funções aqui.
* Todos os arquivos de funções devem ter funções claramente construidas, declaradas e comentadas
* Pode usar váriaveis globais nos arquivos, más tente minimizar essa requisição
___
#### Regras de desenvolvedor
* Nunca commite code não testado;
* Se seu code funciona, más quebra outro, suas escolhas são, não commitar e esperarem ajustar o determinado trecho ou commitar e quebrar o trecho;
* Evite mexer na estrutura do XML, se necessário, envie a alterações junto com o code necessário para essa alterações, no mesmo push;
* Não envie "code velho" no seu push, sempre deixe a branch atualizada antes de dar o commit;
* Toda a alterações sobre o font do PF deve ser feito em um git local e depois requisitado o push para um commiter do projeto;
* Se corrigir algum problema, mande no readme do push o ticket referente ao problema;
* Ajuste o envio de push dessa forma:
	* Primeira frase breve -> Titulo;
	* Descreva a ação (Delete, add e demais);
	* Coloque o ticket alvo se tiver;
	* Tenha no máximo 72 colunas por linha;
* Sempre que colocar code shell, use caminhos absolutos nos comandos ou arquivos;
___
#### Regras de HTML
* Não mande code HTML quebrado, o compilador reclama
* O PF usa o Doctype XHTML no WebGUI, este segue essas regras:
	* Use só lowercase;
	* As tags ```<img />``` sempre devem ser fechadas
	* Tags que se fecham tem que ter um espaço no /
	* Toda a tag img deve ter um alt mesmo não contento mensagem
	* O E-Comercial (&) em HTML deve sempre ser representado pelo ```&amp```
	* As seguintes tags não podem ter atributos name: ```table, div, ul e li```
	* Atributos de caracteristicas, como required e demais, devem ser representados dessa forma: ```required="required"```
	* Toda tag de tipo de ação deve ter um type especificando ação e em minusculo, Ex: ```input type="text"```
	* Todas as tags não inlines, devem ter um fechamento
	* A tag table não pode ter um ```<form>``` no seu interior
	* Se quiser um JS em algum ponto, use: ```script type="text/javascript"```
	* Em eventos de JS, sempre deixe em minusculo o nome do evento
___
#### Regras de PHP
* Só quebre as regras somente quando necessário e comente o trecho -> Necessita de uma justificativa
* Todo o arquivo deve ter um cabeçalho descrevendo
* Use váriaveis em inglês, sempre em minuscculo com espaçamento em underline ou em camelCase
* Quando for colocar uma váriavel em uma string, use: ```"teste{$test}"``` para montar a tag
* Se precisar comentar algum lugar, comente em ingles e somente oq é verdadeiramente importante
* Para comentarios em linha unica, use // e para comentários em várias linhas, use /**/, nunca use #
* Só use ```elseif``` quando necessário, se houver mais condições troque para switch case e esse sempre deve ter um default como escape
* Adicione o comentario ```TODO:``` em trechos que necessita de algo a ser feito, use ```FIXME:``` em trechos com problemas e use ```NOTE:``` em trechos que necessita explicar e esse algo tem que ser importante, tipo ```ǸOTE: Não mexa aqui, vai dar ruim```
* Simplifique sempre que puder, deixe sempre limpo, resumido e nunca crie variaveis desnecessarias ou de uso unico
* Nunca use a váriavel $g para qualquer coisa, essa é de sistema
* Se usar class, crie variaveis com seu nivel de visibilidade bem definido
* Evite uso de funções alias, use sempre a original daquela função
___
#### Estilo de recuo
* Sempre feche uma estrutura de loop ou decisão com chaves, mesmo só tendo uma instrução
* Em instruções condicionais, recue 4 colunas após a primeira linha
* Não deixe espaços em argumentos de funções, somente se a mesma tiver mais um argumento
* Não misture espaços com tabs, somente no caso já comentado
* Espaçamento é definido em 8, recuos de 4 somente para a situação já comentada
* Não deixe espaços ou tabs em branco nas linhas, mesmo que for uma linha vazia
___
#### Manipulaçãode configuração
* De unset em todas as várias que forem bool false, trate essa condição
___
#### Regras de JS
* Não use o JS para fazer o PF funcionar em navegadores mais antigos
* JS puro resolve várias coisas, más o PF já vem com libs como Bootstrap e Jquery, se elas resolverem algo para você , use, facilite sua vida;
* O PF não usa ```transpiler``` ou utilitarios semelhantes
* Evite usar o JS em situações de login para não criar vulnerabilidades
___
#### SHELL
* Use chaves para todas as referencias a variaveis globais em SHELL, Ex: ```${TESTE}```
___
#### Code externo
* Não precisa ser passado pelas regras descritas, porém, se for adicionar no repo principal, ai sim, ai tem que passar por uma revisão para implementação
___
### P.S: 
#### Não coloquei sobre o PORT's pq não achei necessário para esse resumo
