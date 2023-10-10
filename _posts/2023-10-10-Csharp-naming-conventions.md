---
title: "C# Naming Conventions"
date: 2023-10-10  21:12:00 +0900
categories: [C#]
tags: [C#, en] #lang tag: en, jp, zh
---

```csharp
/// C# Naming Conventions
/// C#コーディングルール

// Using PascalCase for class name
public class PlayerController					
{
	// Using an underscore and camelCase for private field names
    private int _playerHealth; 					
	
	// Using PascalCase for public fields (Not recommended)
	public int PlayerHealth;	
	// Recommended way: Using Properties				
	public int PlayerHealth { get; set; }		
	
	// Using PascalCase for constant names
	public const int MaxHealth = 10;			
	
	// Using PascalCase for method names 
	// and camelCase for parameter names
	public void MovePlayer(Position playerPos)	
   	{                                           
        // Function logic here
   	}
	
	// Using PascalCase for enum type
	public enum PlayerStatus					
	{
		Active,
		Inactive,
		Banned
	}

	// Using PascalCase for struct names
	public struct Position						
	{
		public int X;
		public int Y;
	}
	
	// Using PascalCase for interface names
	public interface IOrderService				
	{
		void PlaceOrder();
	}
}
```