# Sistema Bancário em Python

Este é um sistema bancário simples implementado em Python, que permite a criação de contas, realização de depósitos e saques, e o registro de transações.

## Estrutura do Código

### Classes

1. **Cliente**
   - Representa um cliente do banco.
   - Atributos:
     - `endereco`: Endereço do cliente.
     - `contas`: Lista de contas associadas ao cliente.
   - Métodos:
     - `realizar_transacao(conta, transacao)`: Realiza uma transação em uma conta.
     - `adicionar_conta(conta)`: Adiciona uma conta à lista de contas do cliente.

2. **PessoaFisica (herda de Cliente)**
   - Representa um cliente pessoa física.
   - Atributos:
     - `nome`: Nome do cliente.
     - `data_nascimento`: Data de nascimento do cliente.
     - `cpf`: CPF do cliente.
   - Método: Construtor para inicializar os atributos de pessoa física.

3. **Conta**
   - Representa uma conta bancária genérica.
   - Atributos:
     - `_saldo`: Saldo da conta.
     - `_numero`: Número da conta.
     - `_agencia`: Agência da conta.
     - `_cliente`: Cliente associado à conta.
     - `_historico`: Histórico de transações da conta.
   - Métodos:
     - `nova_conta(cls, cliente, numero)`: Método de classe para criar uma nova conta.
     - `sacar(valor)`: Realiza um saque na conta.
     - `depositar(valor)`: Realiza um depósito na conta.

4. **ContaCorrente (herda de Conta)**
   - Representa uma conta corrente.
   - Atributos:
     - `limite`: Limite de saque.
     - `limite_saques`: Limite de número de saques.
   - Métodos:
     - `sacar(valor)`: Realiza um saque na conta corrente, considerando o limite de saque e o número de saques.

5. **Historico**
   - Representa o histórico de transações de uma conta.
   - Atributos:
     - `_transacoes`: Lista de transações.
   - Métodos:
     - `adicionar_transacao(transacao)`: Adiciona uma transação ao histórico.

6. **Transacao (classe abstrata)**
   - Representa uma transação bancária.
   - Métodos abstratos:
     - `valor`: Retorna o valor da transação.
     - `registrar(conta)`: Registra a transação em uma conta.

7. **Saque (herda de Transacao)**
   - Representa um saque.
   - Atributos:
     - `_valor`: Valor do saque.
   - Métodos:
     - `registrar(conta)`: Registra o saque em uma conta, atualizando o saldo e o histórico.

8. **Deposito (herda de Transacao)**
   - Representa um depósito.
   - Atributos:
     - `_valor`: Valor do depósito.
   - Métodos:
     - `registrar(conta)`: Registra o depósito em uma conta, atualizando o saldo e o histórico.

### Exemplo de Uso

```python
# Criação de um cliente Pessoa Física
cliente = PessoaFisica(nome="João", data_nascimento="01/01/1980", cpf="12345678900", endereco="Rua A, 123")

# Criação de uma conta corrente para o cliente
conta = ContaCorrente.nova_conta(cliente, "1234")
cliente.adicionar_conta(conta)

# Realização de um depósito
deposito = Deposito(1000)
cliente.realizar_transacao(conta, deposito)

# Realização de um saque
saque = Saque(200)
cliente.realizar_transacao(conta, saque)

# Exibição de informações da conta e histórico de transações
print(conta)
for transacao in conta.historico.transacoes:
    print(transacao)
```

### Saída Esperada

```
Agência:    0001
C/C:        1234
Titular:    João

{'tipo': 'Deposito', 'valor': 1000, 'data': 'DD-MM-YYYY HH:MM:SS'}
{'tipo': 'Saque', 'valor': 200, 'data': 'DD-MM-YYYY HH:MM:SS'}
```

## Instalação e Execução

1. Certifique-se de ter o Python instalado na sua máquina.
2. Salve o código em um arquivo, por exemplo, `banco.py`.
3. Execute o arquivo com o comando: `python banco.py`.

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para fazer um fork do repositório e enviar pull requests.

