using System;
using System.Collections.Generic;

interface IInventoryItem
{
    string Name { get; set; }
    int Volume { get; set; }
}

class InventoryItem : IInventoryItem
{
    public string Name { get; set; }
    public int Volume { get; set; }
}

class Inventory : IInventory
{
    private List<IInventoryItem> items = new List<IInventoryItem>();
    private const int MAX_VOLUME = 44330;
    private bool drillsOn = true;

    public void AddItem(IInventoryItem item)
    {
        if (GetCurrentInventoryVolume() + item.Volume <= GetMaxInventoryVolume())
        {
            items.Add(item);
            Console.WriteLine(item.Name + " added to inventory.");

            // Check if inventory capacity has reached 44330 L and turn off drills
            if (GetCurrentInventoryVolume() == MAX_VOLUME && drillsOn)
            {
                Console.WriteLine("Inventory capacity has reached 44330 L, turning off drills on the ship.");
                drillsOn = false;
            }
        }
        else
        {
            Console.WriteLine("Inventory is full.");
        }
    }

    public int GetCurrentInventoryVolume()
    {
        int currentVolume = 0;
        foreach (var item in items)
        {
            currentVolume += item.Volume;
        }
        return currentVolume;
    }

    public int GetMaxInventoryVolume()
    {
        return 100;
    }
}

interface IInventory
{
    void AddItem(IInventoryItem item);
    int GetCurrentInventoryVolume();
    int GetMaxInventoryVolume();
}

class Program
{
    static void Main(string[] args)
    {
        IInventory inventory = new Inventory();

        InventoryItem item1 = new InventoryItem { Name = "Item1", Volume = 30 };
        InventoryItem item2 = new InventoryItem { Name = "Item2", Volume = 40 };
        InventoryItem item3 = new InventoryItem { Name = "Item3", Volume = 50 };

        inventory.AddItem(item1);
        inventory.AddItem(item2);
        inventory.AddItem(item3);
    }
}





Errors---------------------------

Program(26,44): Error: ) expected
Program(1,0): Error: A using clause must precede all other elements defined in the namespace except extern alias declarations Program(2,0): Error: A using clause must precede all other elements defined in the namespace except extern alias declarations
Program(80,0): Error: Type or namespace definition, or end-of-file expected
Program(65,6): Error: The namespace ' already contains a definition for 'Program'
Program(27,12): Error: The type or member 'Console' is prohibited Program(27,20): Error: The type or member 'void
Console.WriteLine(string value)' is prohibited
Program(32,62): Error: The type or member 'Console' is prohibited Program(32,70): Error: The type or member 'void
Console.WriteLine(string value)' is prohibited
Program(38,58): Error: The type or member 'Console' is prohibited Program(38,66): Error: The type or member 'void Console.WriteLine(string value)' is prohibited
