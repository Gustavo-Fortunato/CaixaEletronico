# CaixaEletronico



## CODE
using System;
Console.BackgroundColor = ConsoleColor.DarkGreen;
Console.WriteLine("##  Bem-vindo ao Caixa Eletrônico  ##");
Console.BackgroundColor = ConsoleColor.Black;
Console.WriteLine("------------------------------------------------");
Console.BackgroundColor = ConsoleColor.DarkBlue;

int qtde100, qtde50, qtde20, qtde10;
int valorSaque, valorRestoTotal;

Console.WriteLine("# Informe a quantidade de cédulas de cem: ");
Console.BackgroundColor = ConsoleColor.Red;
qtde100 = int.Parse(Console.ReadLine());

Console.BackgroundColor = ConsoleColor.DarkBlue;
Console.WriteLine("# Informe a quantidade de cédulas de cinquenta: ");
Console.BackgroundColor = ConsoleColor.Red;
qtde50 = int.Parse(Console.ReadLine());

Console.BackgroundColor = ConsoleColor.DarkBlue;
Console.WriteLine("# Informe a quantidade de cédulas de vinte: ");
Console.BackgroundColor = ConsoleColor.Red;
qtde20 = int.Parse(Console.ReadLine());

Console.BackgroundColor = ConsoleColor.DarkBlue;
Console.WriteLine("# Informe a quantidade de cédulas de dez: ");
Console.BackgroundColor = ConsoleColor.Red;
qtde10 = int.Parse(Console.ReadLine());

//VARIAVEL AUXILIAR PARA CONTROLE DE FLUXO
bool play = true;

//CALCULAR O VALOR TOTAL DO CAIXA DE ACORDO COM QTDE DE CÉDULAS
int valorTotalCaixa = (qtde100 * 100) + (qtde50 * 50) + (qtde20 * 20) + (qtde10 * 10);

while (play) {
    Console.BackgroundColor = ConsoleColor.Black;
    Console.WriteLine("----------------------------------------------------------------------------");
    Console.ForegroundColor = ConsoleColor.White;
    Console.BackgroundColor = ConsoleColor.Red;
    
    Console.WriteLine("Obrigado! Agora digite o valor que deseja sacar: ");
    Console.BackgroundColor = ConsoleColor.Black;
    valorSaque = int.Parse(Console.ReadLine());
    Console.BackgroundColor = ConsoleColor.DarkBlue;
    if(valorTotalCaixa < valorSaque)
    {
        Console.BackgroundColor = ConsoleColor.Red;
        Console.WriteLine("Valor indisponível no caixa, tente novamente!");
        Console.WriteLine("O valor disponível no caixa-eletrônico é: " + valorTotalCaixa);
        Console.BackgroundColor = ConsoleColor.Green;
        Console.WriteLine("Deseja realizar outro saque? (S/N)");
        string resposta = Console.ReadLine();
        Console.BackgroundColor = ConsoleColor.Black;
        if (resposta == "N" || resposta == "n")
        {
            return;
        }
        else
        {
            while (valorTotalCaixa < valorSaque)
            {
                Console.WriteLine("----------------------------------------------------------------------------");
                Console.ForegroundColor = ConsoleColor.White;
                Console.BackgroundColor = ConsoleColor.Red;
                
                Console.WriteLine("Obrigado! Agora digite o valor que deseja sacar: ");
                Console.BackgroundColor = ConsoleColor.Green;
                valorSaque = int.Parse(Console.ReadLine());
                Console.BackgroundColor = ConsoleColor.Black;
                if (valorSaque >= valorTotalCaixa)
                {
                    continue;
                }
            }
        }
        
    }
    int ced100, ced50, ced20, ced10;
    
    Console.BackgroundColor = ConsoleColor.Green;
    Console.WriteLine("Calculando, aguarde...");
    Console.BackgroundColor = ConsoleColor.Black;

    bool fluxo100 = false;
    bool fluxo50 = false;
    bool fluxo20 = false;
    bool fluxo10 = false;
    
  
    ced100 = Convert.ToInt32(valorSaque / 100);
    if (qtde100 >= ced100 && valorSaque > 100)
    {  
        qtde100 -= ced100;
        valorRestoTotal = valorSaque - (100 * ced100);
    
        ced50 = valorRestoTotal / 50;
        qtde50 -= ced50;
        valorRestoTotal -= (50 * ced50);
    
        ced20 = valorRestoTotal / 20;
        qtde20 -= ced20;
        valorRestoTotal -= (20 * ced20);
    
        ced10 = valorRestoTotal / 10;
        qtde10 -= ced10;
        valorRestoTotal -= (10 * ced10);

        Console.BackgroundColor = ConsoleColor.DarkBlue;
        Console.WriteLine("Saque realizado! Notas utilizadas - Cem: " + ced100 + " Cinquenta: " + ced50 +
    " Vinte: " + ced20 + " Dez: " + ced10);
        Console.WriteLine("Valor total: " + valorSaque);
        Console.BackgroundColor = ConsoleColor.Black;
        valorTotalCaixa -= Convert.ToInt32(valorSaque);
        fluxo100 = true;
        fluxo50 = true;
        fluxo20 = true;
        fluxo10 = true;

        Console.WriteLine("Deseja realizar outro saque? (S/N)");
        string resposta = Console.ReadLine();
        if (resposta == "N" || resposta == "n")
        {
            play = false;
        } 
    }
    if (qtde50 >= Convert.ToInt32(valorSaque / 50) && !fluxo50) 
    { 
        ced50 = Convert.ToInt32(valorSaque / 50);
        qtde50 -= ced50;
        valorRestoTotal = valorSaque - (50 * ced50);
    
        ced20 = valorRestoTotal / 20;
        qtde20 -= ced20;
        valorRestoTotal -= (20 * ced20);

        ced10 = valorRestoTotal / 10;
        qtde10 -= ced10;
        valorRestoTotal -= (10 * ced10);

        Console.BackgroundColor = ConsoleColor.Black;
        Console.WriteLine("Saque realizado! Notas utilizadas - Cinquenta: " + ced50 +
   " Vinte: " + ced20 + " Dez: " + ced10);
        Console.WriteLine("Valor total: " + valorSaque);
        valorTotalCaixa -= Convert.ToInt32(valorSaque);

        fluxo50 = true;
        fluxo20 = true;
        fluxo10 = true;

        Console.WriteLine("Deseja realizar outro saque? (S/N)");
        string resposta = Console.ReadLine();
        if (resposta == "N" || resposta == "n")
        {
            play = false;
        }

    }

    if (qtde20 >= Convert.ToInt32(valorSaque / 20) && !fluxo50)
    {
        ced20 = Convert.ToInt32(valorSaque / 20);
        qtde20 -= ced20;
        valorRestoTotal = valorSaque - (20 * ced20);
    
        ced10 = Convert.ToInt32(valorRestoTotal / 10);
        qtde10 -= ced10;
        valorRestoTotal -= (10 * ced10);

        Console.WriteLine("Saque realizado! Notas utilizadas - Vinte: " + ced20 + " Dez: " + ced10);
        Console.WriteLine("Valor total: " + valorSaque);
        valorTotalCaixa -= Convert.ToInt32(valorSaque);

        fluxo50 = true;
        fluxo20 = true;
        fluxo10 = true;

        Console.WriteLine("Deseja realizar outro saque? (S/N)");
        string resposta = Console.ReadLine();
        if (resposta == "N" || resposta == "n")
        {
            play = false;
        }
    }
    if (qtde10 >= Convert.ToInt32(valorSaque / 10) && !fluxo20)
    {
        ced10 = Convert.ToInt32(valorSaque / 10);
        qtde10 -= ced10;
        valorRestoTotal = valorSaque % 10;
    }
}
