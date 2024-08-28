# src/agendamento_consultorio.py

import datetime

# Classe para representar um Paciente
class Paciente:
    def __init__(self, nome, cpf, data_nascimento, telefone):
        self.nome = nome
        self.cpf = cpf
        self.data_nascimento = data_nascimento
        self.telefone = telefone

# Classe para representar um Médico
class Medico:
    def __init__(self, nome, crm, especialidade):
        self.nome = nome
        self.crm = crm
        self.especialidade = especialidade

# Classe para representar uma Consulta
class Consulta:
    def __init__(self, paciente, medico, data_hora):
        self.paciente = paciente
        self.medico = medico
        self.data_hora = data_hora

# Lista para armazenar os pacientes, médicos e consultas
pacientes = []
medicos = []
consultas = []

# Função para cadastrar um novo paciente
def cadastrar_paciente():
    nome = input("Nome do Paciente: ")
    cpf = input("CPF do Paciente: ")
    data_nascimento = input("Data de Nascimento (DD/MM/AAAA): ")
    telefone = input("Telefone: ")
    
    paciente = Paciente(nome, cpf, data_nascimento, telefone)
    pacientes.append(paciente)
    print(f"Paciente {nome} cadastrado com sucesso!")

# Função para cadastrar um novo médico
def cadastrar_medico():
    nome = input("Nome do Médico: ")
    crm = input("CRM do Médico: ")
    especialidade = input("Especialidade: ")
    
    medico = Medico(nome, crm, especialidade)
    medicos.append(medico)
    print(f"Médico {nome} cadastrado com sucesso!")

# Função para agendar uma consulta
def agendar_consulta():
    print("Lista de Pacientes:")
    for i, paciente in enumerate(pacientes):
        print(f"{i + 1} - {paciente.nome}")
    
    paciente_idx = int(input("Selecione o paciente pelo número: ")) - 1
    paciente_selecionado = pacientes[paciente_idx]
    
    print("Lista de Médicos:")
    for i, medico in enumerate(medicos):
        print(f"{i + 1} - {medico.nome} ({medico.especialidade})")
    
    medico_idx = int(input("Selecione o médico pelo número: ")) - 1
    medico_selecionado = medicos[medico_idx]
    
    data_hora = input("Data e Hora da Consulta (DD/MM/AAAA HH:MM): ")
    data_hora_obj = datetime.datetime.strptime(data_hora, '%d/%m/%Y %H:%M')
    
    consulta = Consulta(paciente_selecionado, medico_selecionado, data_hora_obj)
    consultas.append(consulta)
    print(f"Consulta marcada para {paciente_selecionado.nome} com o Dr(a). {medico_selecionado.nome} em {data_hora}.")

# Função principal para exibir o menu e processar as opções
def menu():
    while True:
        print("\n--- Sistema de Agendamento de Consultas ---")
        print("1. Cadastrar Paciente")
        print("2. Cadastrar Médico")
        print("3. Agendar Consulta")
        print("4. Sair")
        opcao = input("Escolha uma opção: ")

        if opcao == '1':
            cadastrar_paciente()
        elif opcao == '2':
            cadastrar_medico()
        elif opcao == '3':
            agendar_consulta()
        elif opcao == '4':
            print("Saindo...")
            break
        else:
            print("Opção inválida! Tente novamente.")

if __name__ == "__main__":
    menu()
