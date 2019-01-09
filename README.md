# Extração de agenda de ministro
> Repositório criado para o processo seletivo de estágio em data-mining do sigalei.

## O desafio
Imagine que você trabalha em uma empresa que faz monitoramento legislativo e executivo e que agora está com interesse em dados relacionados a ministros. Para começar a atingir esse objetivo, um primeiro desafio é a extração das informações da agenda do Ministro da Economia, Paulo Guedes.

## Requisitos
A partir da seguinte [página do site do Ministério da Economia](http://www.economia.gov.br/Economia/agendas/gabinete-do-ministro/ministro-da-economia-paulo-guedes):
- Extraia todos os eventos da agenda do ministro desde o ínicio do ano (01/01/2019) até a data mais atual (dia que for rodado o script)
- Você *deve* usar o framework [scrapy (Python)](https://docs.scrapy.org/en/latest/index.html)
- Cada evento da agenda deve ser extraído como um dicionário com os seguintes "campos":
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
MinistryName: "Ministério da Economia",
MinisterName: "Paulo Guedes",
EventDate: "2019-01-07 15:30:00",
EventTitle: "Audiência com Luiz Carlos Trabuco, presidente do Conselho de Administração do Bradesco",
EventLocation: "Ministério da Fazenda",
EventParticipants: ["Adolfo Sachsida, secretário de Política Econômica do Ministério da Economia", "Marco Kohler, sub-Secretário de direito e economia da SPE Octavio Lazari, presidente Executivo da Organização Bradesco"]
}
```
- Incluir um arquivo `README.md` no seu projeto, descrevendo qual versão do Python foi usada, quais bibliotecas precisam ser instaladas (opcionalmente incluia um arquivo `requirements.txt`) e como rodar, além de qualquer outra informação que você achar necessário

## Dicas
- Se você ainda não conhece o Scrapy, provavelmente valha a pena fazer o seguinte [tutorial](https://docs.scrapy.org/en/latest/intro/tutorial.html#) antes de começar esse projeto
- O Scrapy possui seu próprio parser de HTML, sendo que a árvore DOM pode ser acessada usando seletores CSS ou XPATH. Opcionalmente, você pode usar a biblioteca [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) para fazer o parser e a manipulação dos elementos HTML. Apesar de ser (talvez) um pouco mais complexa, ela é muito mais poderosa e permite que você faça uma busca mais refinada na página HTML. Para criar um objeto `soup` a partir do objeto `response` do Scrapy:
```
    def parse(self, response):
        soup = BeautifulSoup(response.body, 'lxml')
```
- Analise com cuidado a URL da página de Agenda do site do Ministério da Economia. Manipulando os parâmetros, você poderá navegar pelo calendário, sem ter que "clicar" em nenhum botão

## Tarefa bônus (Não obrigatória!)
Além dos campos dos objetos extraídos, inclua mais um campo chamado `_id`. Esse campo deverá ser o identificador do evento, e poderá ter o formato que você quiser. Vale ressaltar que o `_id` deve, obviamente, ser único (não se repetir entre os eventos).

**Dica**: Evite identificadores sequenciais, uma vez que novos eventos podem ser inseridos/excluídos/modificados retroativamente

## Critérios de avaliação
- **Escopo**: avaliaremos se o seu projeto está extraindo os campos solicitados da totalidade dos eventos da agenda de Paulo Guedes.
- **Qualidade do código**: nós no sigalei prezamos por códigos bem organizados, simples, sem repetição e com nomes de métodos, variáveis e classes intuitivos. Métodos muito grandes não são uma boa ideia, quebre em vários métodos menores. Uma boa documentação é fundamental, entretanto é melhor fazer um bom código (que consigamos entender apenas olhando para ele), do que enchê-lo de comentários.
- **Execução**: gostaríamos de rodar sua spider para ver o resultado de seu trabalho. Esse critério, entretanto, não é eliminatório. Caso você não consiga fazer um programa funcional, envie mesmo assim.
- **Desafio**: o cumprimento do desafio contará alguns pontos a mais, bem como qualquer incremento no escopo ou uso de técnicas mais avançadas (pipelines, parâmetros, exportação em JSON, etc). Esse critério também não é eliminatório, então não se preocupe se não conseguir ou não tiver tempo de fazer.

## Envio do projeto
O projeto deve ser enviado compactado (`.zip`) para os e-mails caio@sigalei.com.br (com cópia para guilherme.acra@sigalei.com.br e tretinha@sigalei.com.br) com o assunto: Desafio de Mining - SEU NOME até às **23:59 do dia 20/01/2019**.

## Dúvidas
Se tiverem qualquer dúvida, não deixem de entrar em contato com a gente pelo e-mails caio@sigalei.com.br (com cópia para guilherme.acra@sigalei.com.br e tretinha@sigalei.com.br). Algum de nós entrará em contato com você o mais rápido possível. Respostas de perguntas que possam ajudar a todos serão compartilhadas nos e-mail de vocês.
