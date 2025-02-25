
using System;
using System.Collections.Generic;

Console.WriteLine("Bem-vindo ao estacionamento da helice!");

Console.Write("Digite o preço inicial: ");
int preco = int.Parse(Console.ReadLine());

Console.Write("Digite o preço por hora: ");
int precoHora = int.Parse(Console.ReadLine());

List<string> veiculos = new List<string>(); // lista para armazenar placas

while (true)
{
    Console.WriteLine("1 - cadastrar veículo");
    Console.WriteLine("2 - remover veículo");
    Console.WriteLine("3 - listar veículos");
    Console.WriteLine("4 - encerrar");

    int opcao = int.Parse(Console.ReadLine());

    switch (opcao)
    {
        case 1:
            Console.Write("digite a placa do veículo: ");
            veiculos.Add(Console.ReadLine()); // cadastra a placa na lista
            break;

        case 2:
            Console.Write("digite a placa do veículo para remover: ");
            string placaRemovida = Console.ReadLine();

            if (veiculos.Remove(placaRemovida))
            {
                Console.Write("quantas horas o veículo ficou estacionado? ");
                int horas = int.Parse(Console.ReadLine());
                Console.WriteLine($"Veículo {placaRemovida} removido. Total: R$ {(horas * precoHora) + preco}");
            }
            else
            {
                Console.WriteLine("veículo não encontrado.");
            }
            break;

        case 3:
            Console.WriteLine("\nveículos estacionados:");
            if (veiculos.Count == 0)
            {
                Console.WriteLine("nenhum veículo cadastrado.");
            }
            else
            {
                for (int i = 0; i < veiculos.Count; i++) // usando for para listar as placas
                {
                    Console.WriteLine($"Placa: {veiculos[i]}");
                }
            }
            break;

        case 4:
            return; // Encerra o programa

        default:
            Console.WriteLine("opção inválida.");
            break;
    }
}
