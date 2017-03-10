//Rextester.Program.Main is the entry point for your code. Don't change it.

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text.RegularExpressions;

namespace Rextester
{
    class Animal
    {
        string Name { get; set;}
        int steps;
        int Steps 
        {
			get
	        {
				return steps;
	        }
        	set
	        {
	        	var rnd = new Random();
	        	steps = rnd.Next(1, 10);
	        }
	    }
        abstract void Action();
        abstract void Move();
        abstract void Voice();
    }
    
    class Dog : Animal
    {
        public string Name{ get; set;}
        public void Action()
        {
        	Console.WriteLine(Name + " подаёт тебе лапу");
        }
        public void Move()
        {
            Console.WriteLine(Name + " сделал " + Steps + " шага(ов)");
        }
        public void Voice()
        {
            Console.WriteLine(Name + " лает на тебя");
        }
        public void Guard()
        {
            Console.WriteLine(Name + " охраняет тебя");
        }
        public Dog(string name)
        {
            Name = name;
        }
        public Dog()
        {
            Name = "Пёсик";
        }
    }
        
    class Puppy: Dog
    {
        public new void Voice()
        {
            Console.WriteLine(Name + " Тяв! Тяв!");
        }
        public Puppy()
        {
            Name = "Щенок";
        }
    }
    
    class Cat : Animal
    {
        public string Name {get; set;}
        public int Steps{ get; set;}
        public void Action()
        {
        	Console.WriteLine(Name + " трётся о ноги и мурлычет");
        }
        public void Voice()
        {
            Console.WriteLine(Name + " мяу!");
        }
        public void Move()
        {
            Random count = new Random();
            Steps = (int)(count.Next(1, 10));
            Console.WriteLine(Name + " сделал " + Steps + " шага(ов)");
        }
        public void CatchMouse()
        {
            Console.WriteLine(Name + " ловит мышку");
        }
        public Cat(string name)
        { 
            Name = name;
        }
    }
    
    class Program
    { 
        public static void Main(string[] args)
        {
            var num = Console.ReadLine();
            List<Animal> animals = new List<Animal>();
            animals.Add(new Dog("Шарик"));
            animals.Add(new Cat("Феликс"));
            animals.Add(new Dog("Полкан"));
            animals.Add(new Puppy());
            
            foreach (Animal animal in animals)
            {
                if (animal is Dog) 					// проверяем является ли данное животное собакой
                {
                    ((Dog)animal).Guard();
                    animal.Voice();
                    animal.Move();
                    animal.Action();
                }
                else 
                {
                    ((Cat)animal).CatchMouse();
                    animal.Voice();
                }
            }
        }
    }
}
