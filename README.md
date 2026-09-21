1 Lista de exercícios


1. Aquecimento: Crie um script em Python que declare duas variáveis, nível de acesso do usuário e porta destravada, respectivamente dos tipos inteiro e booleano. Em seguida, escreva uma estrutura condicional que verifique o se o nível de acesso é maior ou igual a cinco. Se for, altere a variável porta destravada para indicar que ela está está destravada e imprima a mensagem “acesso liberado”. Caso contrário, imprima “Acesso negado: Permissão insuficiente”.

nivel_acesso = 1
porta_destravada = False
if nivel_acesso >= 5:
    porta_destravada = True
    print("porta destravada, acesso liberado")
else:
    print("porta travada, Acesso negado: Permissão insuficiente")



2. Intermediário: Crie uma função responsável por analisar temperaturas, que recebe como parâmetro uma lista de números ponto flutuante, representando leituras de temperatura de um dia inteiro (ex. [22.5, 25.0, 31.2, 28.4, 19.8]).
A função deve percorrer a lista e calcular:
(a) A temperatura média do dia.
(b) Quantas vezes a temperatura ultrapassou 30.0 graus (alerta de calor). A função deve retornar os dois valores, e o main deve imprimi-los na tela de forma amigável.


def analisar_temperaturas(temperaturas):
    soma = 0
    alertas_calor = 0
    
    for temperatura in temperaturas:
        soma += temperatura

        if temperatura > 30:
            alertas_calor += 1

    media = soma / len(temperaturas)

    return media, alertas_calor
    
def main():
    temperaturas = [22.5, 25.0, 31.2, 28.4, 19.8]

    media, alertas = analisar_temperaturas(temperaturas)

    print(f"temperatura média do dia: {media:.2f}°C")
    print(f"quantidade de alertas de calor: {alertas}")

main()





3. Intermediário 2: Modelagem de dispositivo inteligente: Crie uma classe chamada LumináriaSmart, que deve possuir os atributos que representam o id do dispositivo, se ela está ligada e a intensidade que deve variar entre 0 e 100, com valor padrão zero. Crie um método que inverte o estado atual da luminária, ou seja, se estiver ligada ela deve desligar e vice-versa. Faça uma função para ajustar a intensidade, garantindo que o valor não seja menor do que 0 e nem maior do que 100. Crie uma instância da classe, chame os métodos para ligar a luminária e ajustar a intensidade para 75%, e imprima o estado final do objeto.


class LuminariaSmart:
    def __init__(self, id_dispositivo):
        self.id_dispositivo = id_dispositivo
        self.ligada = False
        self.intensidade = 0

    def inverter_estado(self):
        self.ligada = not self.ligada

    def ajustar_intensidade(self, intensidade):
        if intensidade < 0:
            self.intensidade = 0
        elif intensidade > 100:
            self.intensidade = 100
        else:
            self.intensidade = intensidade

# Criando uma instância
luminaria = LuminariaSmart("LUM001")

# Ligando a luminária
luminaria.inverter_estado()

# Ajustando a intensidade para 75%
luminaria.ajustar_intensidade(75)

# Imprimindo o estado final
print("ID:", luminaria.id_dispositivo)
print("Ligada:", luminaria.ligada)
print("Intensidade:", luminaria.intensidade, "%")


4. Avançado: Hub Central de gerenciamento da rede de dispositivos inteligentes.
(a) Crie uma classe chamada DispositivoIoT com os atributos para armazenamento do nome e da quantidade de bateria, que deve oscilar entre zero e cem.
(b) Crie uma classe chamada HubCentral, que possua um atributo para indicar os dispositivos conectados (lista vazia inicialmente) e um método para adicionar dispositivos que recebe um dispositivo como parâmetro, para inserir os dispositivos na lista.
(c) Crie um método chamado relatorio_bateria_baixa(), que deve iterar sobre a lista de dispositivos conectados e crie uma string com o nome de todos os dispositivos, cuja bateria esteja abaixo de vinte porcento.
(d) Crie ao menos três instâncias dos dispositivos iot com diferentes níveis de bateria, e os adicione ao hub centra. Execute o relatório.





class DispositivoIoT: 
    def __init__(self, nome, bateria):
        self.nome = nome

    # Garante que a bateria fique entre 0 e 100
        if bateria < 0:
            self.bateria = 0
        elif bateria > 100:
            self.bateria = 100
        else: 
            self.bateria = bateria

class HubCentral:
        def __init__(self):
            self.dispositivos = []

        def adicionar_dispositivo(self,dispositivo):
            self.dispositivos.append(dispositivo)

        def relatorio_bateria_baixa(self):
            relatorio = ""

            for dispositivo in self.dispositivos:
                if dispositivo.bateria < 20:
                    relatorio += dispositivo.nome + "\n"

            return relatorio 

# Criando os dispositivos
lampada = DispositivoIoT("Luminária", 15)
sensor = DispositivoIoT("Sensor de Temperatura", 75)
camera = DispositivoIoT("Câmera", 10)

# Criando o Hub Central
hub = HubCentral()

# Adicionando os dispositivos ao Hub
hub.adicionar_dispositivo(lampada)
hub.adicionar_dispositivo(sensor)
hub.adicionar_dispositivo(camera)

# Executando o relatório
print("Dispositivos com bateria baixa:")
print(hub.relatorio_bateria_baixa())
