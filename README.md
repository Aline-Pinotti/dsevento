### Formação Desenvolvedor Moderno
### Módulo: Back end
### Capítulo: Modelo de domínio e ORM
# DESAFIO:  Modelo de domínio e ORM
*https://devsuperior.com.br/*


Você deve criar um projeto no Spring Boot com Java e banco de dados H2, e implementar o modelo conceitual conforme especificação a seguir. Além disso, você deve fazer o seeding da base de dados conforme diagrama de objetos que segue.

<b>Como o trabalho será corrigido?</b>
O repositório do Github será clonado pelo professor, que executará o projeto localmente. O projeto deverá executar sem erros, e a base de dados deverá ser criada corretamente. O H2 Console será executado no navegador, e todas tabelas esperadas deverão ser criadas, com todos relacionamentos, e os dados do seeding deverão estar presentes em cada tabela.

<b>ESPECIFICAÇÃO - Sistema EVENTO:</b>
Deseja-se construir um sistema para gerenciar as informações dos participantes das atividades de um evento acadêmico. As atividades deste evento podem ser, por exemplo, palestras, cursos, oficinas práticas, etc. Cada atividade que ocorre possui nome, descrição, preço, e pode ser dividida em vários blocos de horários (por exemplo: um curso de HTML pode ocorrer em dois blocos, sendo necessário armazenar o dia e os horários de início de fim do bloco daquele dia). Para cada participante, deseja-se cadastrar seu nome e email.


```mermaid

classDiagram
direction TB
    class Atividade {
	    -~~ oid ~~Integer id
	    -String nome
	    -String descricao
	    -Double preco
    }

    class Participante {
	    -~~ oid ~~Integer id
	    -String nome
	    -String email
    }

    class Bloco {
	    -~~ oid ~~Integer id
	    -Instant inicio
	    -Instant fim
    }

    class Categoria {
	    -~~ oid ~~Integer id
	    -String descricao
    }

    Participante "*      -participantes" -- "1..*       -atividades" Atividade
    Bloco "1..*       -blocos" -- "1   -atividade" Atividade
    Categoria "- categoria       1" -- "atividades       *" Atividade

	style Atividade :,stroke-width:1px,stroke-dasharray:none,stroke:#374D7C,fill:#E2EBFF,color:#374D7C,margin-top:200px,stroke-width:1px,stroke-dasharray:none,stroke:#374D7C,fill:#E2EBFF,color:#374D7C,stroke-width:1px,stroke-dasharray:none,stroke:#374D7C,fill:#E2EBFF,color:#374D7C,stroke-width:1px,stroke-dasharray:none,stroke:#374D7C,fill:#E2EBFF,color:#374D7C
	style Participante :,margin-top:200px,stroke-width:1px,stroke-dasharray:none,stroke:#374D7C,fill:#E2EBFF,color:#374D7C
	style Bloco :,margin-top:200px,stroke-width:1px,stroke-dasharray:none,stroke:#374D7C,fill:#E2EBFF,color:#374D7C
	style Categoria :,margin-top:200px,stroke-width:1px,stroke-dasharray:none,stroke:#374D7C,fill:#E2EBFF,color:#374D7C

	class Atividade:::SkyAtv
	class Participante:::Sky
	class Bloco:::Sky
	class Categoria:::Sky

```

Instância dos dados para *seeding*:

![alt text](imageSeeding.png)