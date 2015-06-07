A ideia desse projeto eh criar uma arquitetura independente de tecnologias que se baseiem em configs com JSON e funcoes em JS puro para serem re-aproveitadas no FRONT e no BACK.

Para isso precisamos definir a estrutura padrao das partes:

- Validacao: deve ser criado uma funcao em JS puro para validar cada campo, por exemplo no Mongoose, e essa mesma função seja re-utilizada no Front, por exemplo no Angular
- Schema: deve ser criado um Schema para cada modulo que sera re-aproveitado tanto no Front como nos testes.
- Testes: deve pegar automaticamente o Schema de cada modulo e rodar os testes em cima de:
    + tipo de cada campo
    + validacao de cada campo
    + retorno corretor das funcoes
- Services: serao a camada acima das chamadas do banco, ja que o modulo pode usar qualquer banco e eles serao chamados nos Controllers
- Controllers: sao os gerenciadores das acoes de cada modulo, basicamente ele eh chamado dentro de uma rota e usa o Service para acoes com o banco
- Rotas: baseada num JSON deve criar toda a API para o CRUD de cada modulo
- Views: views padrao para do CRUD
- Comunicacao: sera feita via REST utilizando uma API comum de CRUD para todos modulos, as rotas adicionais serao descobertas e usada pelos modulos consuindo o JSON q define as rotas para q um modulo nao precise pre-conhecer outro. **Pensar melhor nessa area pois eh a principal**. Precisamos 