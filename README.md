## Qustões do teste da Target Sistemas

### 1) Observe o trecho de código:

int INDICE = 12, SOMA = 0, K = 1;

enquanto K < INDICE faça

{ K = K + 1; SOMA = SOMA + K;}

imprimir(SOMA);

Ao final do processamento, qual será o valor da variável SOMA?

R: O valor da variável será 77

### 2) Descubra a lógica e complete o próximo elemento:

a) 1, 3, 5, 7, ___ = 9

b) 2, 4, 8, 16, 32, 64, ____ = 128

c) 0, 1, 4, 9, 16, 25, 36, ____ = 49

d) 4, 16, 36, 64, ____ = 100

e) 1, 1, 2, 3, 5, 8, ____ = 13

f) 2, 10, 12, 16, 17, 18, 19, ____ = 200

### 3) Dado um vetor que guarda o valor de faturamento diário de uma distribuidora de todos os dias de um ano, faça um programa, na linguagem que desejar, que calcule e retorne:

- O menor valor de faturamento ocorrido em um dia do ano;
- O maior valor de faturamento ocorrido em um dia do ano;
- Número de dias no ano em que o valor de faturamento diário foi superior à média anual.

#### a) Considerar o vetor já carregado com as informações de valor de faturamento.
#### b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média.
#### c) Utilize o algoritmo mais veloz que puder definir.

void main() {
  // faturamentos do ano
  List<double> faturamento = [
    100.0, 200.0, 0.0, 300.0, 0.0, 400.0, 500.0,
  ];

  // faturamentos > 0
  List<double> diasValidos = faturamento.where((dia) => dia > 0).toList();

  // return caso todos serem menos que zero
  if (diasValidos.isEmpty) {
    print('Nenhum dia com faturamento registrado.');
    return;
  }

  // menor e maior faturamentos
  double menorFaturamento = diasValidos.reduce((a, b) => a < b ? a : b);
  double maiorFaturamento = diasValidos.reduce((a, b) => a > b ? a : b);

  // média de faturamento
  double mediaFaturamento = diasValidos.reduce((a, b) => a + b) / diasValidos.length;

  // dias com faturamento > média
  int diasAcimaDaMedia = diasValidos.where((dia) => dia > mediaFaturamento).length;

  print('Menor valor de faturamento: $menorFaturamento');
  print('Maior valor de faturamento: $maiorFaturamento');
  print('Número de dias com faturamento acima da média: $diasAcimaDaMedia');
}


### 4) Banco de dados - Uma empresa solicitou a você um aplicativo para manutenção de um cadastro de clientes. Após a reunião de definição dos requisitos, as conclusões foram as seguintes:

- Um cliente pode ter um número ilimitado de telefones;
- Cada telefone de cliente tem um tipo, por exemplo: comercial, residencial, celular, etc. O sistema deve permitir cadastrar novos tipos de telefone;
- A princípio, é necessário saber apenas em qual estado brasileiro cada cliente se encontra. O sistema deve permitir cadastrar novos estados;

Você ficou responsável pela parte da estrutura de banco de dados que será usada pelo aplicativo. Assim sendo:

- Proponha um modelo lógico para o banco de dados que vai atender a aplicação. Desenhe as tabelas necessárias, os campos de cada uma e marque com setas os relacionamentos existentes entre as tabelas;
- Aponte os campos que são chave primária (PK) e chave estrangeira (FK);
- Faça uma busca utilizando comando SQL que traga o código, a razão social e o(s) telefone(s) de todos os clientes do estado de São Paulo (código “SP”);

Tabelas:

Tabela clientes:
Campos:
id_cliente (PK)
razao_social
id_estado (FK)

Tabela telefones:
Campos:
id_telefone (PK)
numero_telefone
id_cliente (FK)
id_tipo_telefone (FK)

Tabela tipos_telefone
Campos:
id_tipo_telefone (PK)
descricao_tipo

Tabela estados:
Campos:
id_estado (PK)
nome_estado
sigla_estado

Diagrama Relacional (Representação):
clientes (1) ⟶ (N) telefones
telefones (N) ⟶ (1) tipos_telefone
clientes (N) ⟶ (1) estados

Relacionamentos:

A tabela clientes está relacionada com a tabela telefones por meio de id_cliente.
A tabela telefones está relacionada com a tabela tipos_telefone por meio de id_tipo_telefone.
A tabela clientes está relacionada com a tabela estados por meio de id_estado.

SQL de Busca:

SELECT c.id_cliente, c.razao_social, t.numero_telefone
FROM clientes c
JOIN telefones t ON c.id_cliente = t.id_cliente
JOIN estados e ON c.id_estado = e.id_estado
WHERE e.sigla_estado = 'SP';



### 5) Dois veículos, um carro e um caminhão, saem respectivamente de cidades opostas pela mesma rodovia. O carro, de Ribeirão Preto em direção a Barretos, a uma velocidade constante de 90 km/h, e o caminhão, de Barretos em direção a Ribeirão Preto, a uma velocidade constante de 80 km/h. Quando eles se cruzarem no percurso, qual estará mais próximo da cidade de Ribeirão Preto?

#### a) Considerar a distância de 125km entre a cidade de Ribeirão Preto <-> Barretos.
#### b) Considerar 3 pedágios como obstáculo e que o carro leva 5 minutos a mais para passar em cada um deles, pois ele não possui dispositivo de cobrança de pedágio.
#### c)Explique como chegou no resultado. <br>

velocidade médica do carro considerando os pedágios: 125/((125/90) + 0.25) = 89.93 km/h

Velocidade relativa carro e caminhão: 89.93 + 80 = 169.93 km/h

Tempo pra se cruzarem: 125/169.93 = 0.735 horas = 44.1 minutos

Distancia percorrida pelo carro quando se cruzarem: 89.92/0.735 = 66.14 km
Distancia percorrida pelo caminhão quando se cruzarem: 80/0.735 = 58.8km

Explicação: 
Levando em conta que o carro irá parar algumas vezes por conta dos pedágios, o caminhão terá percorrido mais distância. Mesmo o carro sendo mais rápido

