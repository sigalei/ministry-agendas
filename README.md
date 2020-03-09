# Extração da agenda de ministros

## O desafio

Imagine que você mora em um país onde um novo pessoal assumiu o governo e que entre seus amigos há apoiadores e opositores do novo governo.

No grupo de whatsapp dos amigos não param de chegar notícias especulando sobre as atividades do  novo Ministro da Economia, algumas notícias diziam que o Ministro está se encontrando com secretários dos EUA para alugar o Brasil, já outras notícias falavam que o ministro estava se encontrando com outras pessoas para negociar a reforma da previdência justa com a sociedade e fazer o país crescer novamente.

Você, cansado desse desencontro de notícias, decide, por conta própria, descobrir a verdade a partir dos dados oficiais relacionados a agenda do Ministro.

Como estudo de caso e para começar a atingir esse objetivo, um primeiro desafio é a extração das informações da agenda do Ministro da Economia da República Federativa do Brasil, Paulo Guedes.

## Requisitos

A partir da seguinte [página do site do Ministério da Economia](http://www.economia.gov.br/agendas/gabinete-do-ministro/ministro-da-economia/paulo-guedes):

* Extraia todos os eventos da agenda do ministro desde o ínicio do ano (01/01/2020) até a data mais atual (dia que for rodado o script)
* Você *deve* usar o framework [scrapy (Python)](https://docs.scrapy.org/en/latest/index.html)
* Cada evento da agenda deve ser extraído como um dicionário com os seguintes "campos":

``` 
MinistryName        (String, nome do ministério)
MinisterName        (String, nome do ministro)
EventDate           (Datetime, data e hora do evento: AAAA-MM-DD HH:MM:SS)
EventTitle          (String, título do evento)
EventLocation       (String, local do evento)
EventParticipants   (Lista de Strings, participantes do evento - se houver)
```

Por exemplo:

``` 
{
    'MinistryName': 'Ministério da Economia',
    'MinisterName': 'Paulo Guedes',
    'EventDate': '2020-02-13 13:00:00',
    'EventTitle': 'Almoço na Sede da Federação das Indústrias do Estado de São Paulo – Fiesp',
    'EventLocation': 'Av. Paulista, 1313, São Paulo/SP',
    'EventParticipants': [
        'Paulo Skaf – Presidente da Fiesp',
        'Guilherme Afif – Assessor Especial do Ministério da Economia',
        'Samuel Kinoshita – Assessor Especial do Ministério da Economia'
    ]
}
```

* Incluir um arquivo `README.md` no seu projeto, descrevendo qual versão do Python foi usada, quais bibliotecas precisam ser instaladas (opcionalmente incluia um arquivo `requirements.txt` ) e como rodar, além de qualquer outra informação que você achar necessário

## Dicas

* Se você ainda não conhece o Scrapy, provavelmente valha a pena fazer o seguinte [tutorial](https://docs.scrapy.org/en/latest/intro/tutorial.html) antes de começar esse projeto
* O Scrapy possui seu próprio parser de HTML, sendo que a árvore DOM pode ser acessada usando seletores CSS ou XPATH. Opcionalmente, você pode usar a biblioteca [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) para fazer o parser e a manipulação dos elementos HTML (caso queira utilizar, recomendamos que você estude os métodos `select` e `find` ). A princípio ela é um pouco mais complexa, porém é muito mais poderosa e permite que você faça uma busca mais refinada na página HTML. Para criar um objeto `soup` a partir do objeto `response` do Scrapy:
``` 
    def parse(self, response):
        soup = BeautifulSoup(response.body, 'lxml')
```
* Analise com cuidado a URL da página de Agenda do site do Ministério da Economia. Manipulando os parâmetros, você poderá navegar pelo calendário, sem ter que "clicar" em nenhum botão

## Tarefa bônus (Não obrigatória!)

Além dos campos dos objetos extraídos, inclua mais um campo chamado `_id` . Esse campo deverá ser o identificador do evento, e poderá ter o formato que você quiser. Vale ressaltar que o `_id` deve, obviamente, ser único (não se repetir entre os eventos).

**Dica**: Evite identificadores sequenciais, uma vez que novos eventos podem ser inseridos/excluídos/modificados retroativamente

## Critérios de avaliação
* **Escopo**: avaliaremos se o seu projeto está extraindo os campos solicitados da totalidade dos eventos da agenda de Paulo Guedes.
* **Qualidade do código**: nós no Sigalei prezamos por códigos bem organizados, simples, sem repetição e com nomes de métodos, variáveis e classes intuitivos. Métodos muito grandes não são uma boa ideia, quebre em vários métodos menores. Uma boa documentação é fundamental, entretanto é melhor fazer um bom código (que consigamos entender apenas olhando para ele), do que enchê-lo de comentários.
* **Execução**: gostaríamos de rodar sua spider para ver o resultado de seu trabalho. Esse critério, entretanto, não é eliminatório. Caso você não consiga fazer um programa funcional, envie mesmo assim.
* **Desafio**: o cumprimento do desafio contará alguns pontos a mais, bem como qualquer incremento no escopo ou uso de técnicas mais avançadas (pipelines, parâmetros, exportação em JSON, etc). Esse critério também não é eliminatório, então não se preocupe se não conseguir ou não tiver tempo de fazer.

## Envio do projeto

O projeto deve ser enviado compactado ( `.zip` ) para os e-mails guilherme.acra@sigalei.com.br, com cópia para fernando@sigalei.com.br com o assunto: Desafio de Mining - SEU NOME.

## Dúvidas

Se tiverem qualquer dúvida, não deixem de entrar em contato com a gente preferencialmente por mensagem na plataforma do processo seletivo, ou também pelos e-mails guilherme.acra@sigalei.com.br, com cópia para fernando@sigalei.com.br. Algum de nós entrará em contato com você o mais rápido possível. Respostas de perguntas que possam ajudar a todos serão encaminhadas para vocês.
