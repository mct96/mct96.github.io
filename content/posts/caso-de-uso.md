+++
title = 'Caso De Uso'
date = 2024-10-13T15:18:41-04:00
datePublished = 2024-10-13T15:18:41-04:00
draft = false
+++

# Introdução

Neste post, vou descrever alguns pontos interessantes sobre os diagramas de caso
de uso. Não farei uma discussão ou revisão da literatura; apenas abordarei os
aspectos práticos relevantes para a compreensão dos diagramas e seu
propósito. As fontes de informação utilizadas para escrever este post foram
diversos sites, que deixarei como referência. Também utilizei o ChatGPT para
elaborar parte do texto, mas fiz a verificação para garantir a veracidade das
informações fornecidas. Entretanto, caso haja algum erro, peço que entre em
contato comigo pelo e-mail matheuscandido2009@gmail.com informando o erro.

# Origem

O conceito de caso de uso foi introduzido por Ivar Jacobson na década de 1980,
durante seu trabalho na Ericsson. Jacobson desenvolveu essa abordagem como parte
de uma técnica chamada Object-Oriented Software Engineering (OOSE), que buscava
combinar conceitos da programação orientada a objetos com a modelagem de
sistemas. Os casos de uso foram criados como uma maneira de capturar os
requisitos funcionais de um sistema, focando nas interações entre os usuários
(ou "atores") e o sistema, a fim de atingir um objetivo específico.

No início dos anos 1990, a programação orientada a objetos estava ganhando
popularidade, mas havia uma grande diversidade de métodos e técnicas em uso, o
que dificultava a comunicação entre desenvolvedores. Em resposta a isso, três
figuras-chave na engenharia de software — Ivar Jacobson, Grady Booch e James
Rumbaugh — uniram forças para desenvolver a UML. Em 1997, a Object Management
Group (OMG) adotou o UML como padrão para a modelagem de sistemas orientados a
objetos.

Os diagramas de caso de uso foram incluídos na UML como uma das ferramentas
principais para capturar requisitos funcionais. Eles são usados para descrever
como diferentes "atores" interagem com o sistema para realizar tarefas
específicas, enfatizando a visão externa do sistema.

# Importância

A principal importância dos casos de uso (e de diversos diagramas) é que eles
permitem uma comunicação mais clara e inequívoca entre equipes de diferentes
áreas. Em outras palavras, fornecem uma forma de comunicação em que tanto os
desenvolvedores quanto os especialistas de negócios conseguem transmitir suas
ideias sobre o sistema e garantir que os membros de outras áreas também as
compreendam de modo claro.

Isso ocorre porque o diagrama informa a relação/interação entre as
funcionalidades ou atividades sem entrar em detalhes técnicos. Por exemplo, em
vez de dizer que todas as transações devem ser autenticadas por um servidor de
autenticação, o diagrama apenas descreve que as transações precisam ser
autenticadas, independentemente de como isso será feito do ponto de vista
técnico. Isso permite que os clientes compreendam claramente as etapas que o
software deve realizar, sem que seja necessário explicar detalhes técnicos para
eles.

Por fim, os casos de uso podem (e devem) ser usados para gerar requisitos para a
construção do software, pois fornecem, em alto nível, o comportamento desejável
do sistema. Eles indicam quem deve fazer o quê e quais funcionalidades estão
relacionadas.


# Notação

Sem enrolação, o caso de uso contém algumas notações bem simples de
memorizar. Vou descrever cada uma delas, mas tenha em mente que, assim como no
SQL, cada ferramenta possui seu próprio "dialeto", ou seja, a notação pode
variar.

<table>
<tr>
<td>
<img src="/posts/caso-de-uso/ator.png">
</td>
<td>

<p>Representa uma pessoa, sistema ou máquina que está associada a um caso de
uso. Os atores executam um caso de uso e devem estar vinculados a pelo menos
um.</p>

</td>
</tr>

<tr>
<td>
<img src="/posts/caso-de-uso/caso_de_uso.png">
</td>
<td>

<p>Descreve uma função do sistema. Geralmente, o nome é formado pela junção de
um verbo com um substantivo. Por exemplo, a descrição do caso de uso poderia ser
"Fazer Algo". Cada ator deve estar ligado a pelo menos um caso de uso, mas um
caso de uso pode estar associado a vários atores.  </p>

</td>
</tr>


<tr>
<td>
<img src="/posts/caso-de-uso/associacao.png">
</td>
<td>
<p>Indica que um ator realiza um caso de uso</p>
</td>
</tr>

<tr>
<td>
<img src="/posts/caso-de-uso/inclusao.png">
</td>
<td>

<p>É usado para indicar que um caso de uso é uma funcionalidade de outro. Um
caso de uso pode utilizar outro para fazer parte do seu próprio fluxo. Por
exemplo, considere o caso de uso "Comprar Produto", que depende do usuário estar
autenticado. Nesse caso, pode existir um link do tipo <<include>> para o caso de
uso "Autenticar", indicando que o usuário precisa estar autenticado para
realizar o primeiro caso de uso. A seta aponta para o caso de uso principal.</p>

</td>
</tr>

<tr>
<td>
<img src="/posts/caso-de-uso/extensao.png">
</td>
<td>

<p>É usado para indicar que um caso de uso é uma possível extensão de outro, ou
seja, pode haver condições em um caso de uso que levem à execução deste. A seta
aponta para o caso de uso alternativo.</p>
</td>
</tr>

<tr>
<td>
<img src="/posts/caso-de-uso/generalizacao.png">
</td>
<td>
<p>Usado para indicar que um caso de uso herda o comportamento de um caso de uso
base e pode ainda modificar algumas funcionalidades ou adicionar novas. A seta 
aponta para o caso de uso pai.</p>
</td>
</tr>
</table>


# Exemplo

<img src="/posts/caso-de-uso/exemplo.png">

No caso acima, há apenas um ator, *Cliente*, e, através da associação (a linha
contínua), é possível observar que ele só pode executar um caso de uso
(*Reservar Quarto*). O caso de uso *Reservar Quarto*, por sua vez, inclui três
outros casos de uso, a saber: *Verificar Disponibilidade*, *Validar
Documentação* e *Efetuar o Pagamento*. Esses includes indicam que esses casos de
uso são executados quando o caso de uso principal, *Reservar Quarto*, é
executado. Já os casos de uso *Sem Disponibilidade* e *Documentação Inválida*
são <<extends>> de outros casos de uso, o que indica que eles podem ser
executados se alguma condição ocorrer no caso de uso principal. Por fim, o caso
de uso *Efetuar o Pagamento* possui dois "filhos", *Pagar - Dinheiro* e *Pagar -
Débito*, indicando que eles são especializações do caso de uso pai, e que cada
um tem um tratamento próprio, evidenciado através da relação de generalização.

