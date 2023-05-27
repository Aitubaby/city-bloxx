# city-bloxx
using System;

class CityBloxxGame
{
    static int score = 0;
    static int towerHeight = 0;

    static void BuildTower()
    {
        towerHeight++;
    }

    static void DropBlock()
    {
        Random random = new Random();
        int blockPosition = random.Next(1, 4);
        if (blockPosition == towerHeight)
        {
            score++;
            BuildTower();
        }
        else
        {
            Console.WriteLine("Игра окончена. Ваш счет: " + score);
            RestartGame();
        }
    }

    static void RestartGame()
    {
        score = 0;
        towerHeight = 0;
        Console.WriteLine("Начать новую игру? (да/нет)");
        string answer = Console.ReadLine();
        if (answer.ToLower() == "да")
        {
            PlayGame();
        }
        else
        {
            Console.WriteLine("До свидания!");
        }
    }

    static void PlayGame()
    {
        Console.WriteLine("Добро пожаловать в игру City Bloxx!");
        Console.WriteLine("Цель игры - строить башню, выпуская блоки в нужный момент.");
        Console.WriteLine("Чтобы выпустить блок, введите 'выпустить'.");
        Console.WriteLine("Готовы? Нe че джигиттер погнали!");

        while (true)
        {
            string command = Console.ReadLine();
            if (command.ToLower() == "выпустить")
            {
                DropBlock();
            }
            else
            {
                Console.WriteLine("Неверная команда. Введите 'выпустить'.");
            }
        }
    }

    static void Main(string[] args)
    {
        PlayGame();
    }
}
