package com.expensetracker;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

// Expense class to represent individual expenses
class Expense {
    private String description;
    private double amount;
    private String category;

    public Expense(String description, double amount, String category) {
        this.description = description;
        this.amount = amount;
        this.category = category;
    }

    @Override
    public String toString() {
        return String.format("%s - $%.2f (%s)", description, amount, category);
    }

    public double getAmount() {
        return amount;
    }

    public String getCategory() {
        return category;
    }
}

// ExpenseManager class to manage expenses
class ExpenseManager {
    private List<Expense> expenses = new ArrayList<>();

    public void addExpense(Expense expense) {
        expenses.add(expense);
    }

    public void viewExpenses() {
        if (expenses.isEmpty()) {
            System.out.println("No expenses recorded.");
        } else {
            expenses.forEach(System.out::println);
        }
    }

    public void deleteExpense(int index) {
        if (index >= 0 && index < expenses.size()) {
            expenses.remove(index);
            System.out.println("Expense deleted.");
        } else {
            System.out.println("Invalid index.");
        }
    }

    public void summarizeExpenses() {
        double total = expenses.stream().mapToDouble(Expense::getAmount).sum();
        System.out.printf("Total Expenses: $%.2f%n", total);
    }
}

// Main class for console application
public class ExpenseTrackerApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ExpenseManager manager = new ExpenseManager();
        String command;

        System.out.println("Welcome to the Personal Expense Tracker!");

        do {
            System.out.println("\nOptions: add, view, delete, summary, exit");
            command = scanner.nextLine().toLowerCase();

            switch (command) {
                case "add":
                    System.out.print("Description: ");
                    String desc = scanner.nextLine();
                    System.out.print("Amount: ");
                    double amount = Double.parseDouble(scanner.nextLine());
                    System.out.print("Category: ");
                    String category = scanner.nextLine();
                    manager.addExpense(new Expense(desc, amount, category));
                    break;

                case "view":
                    manager.viewExpenses();
                    break;

                case "delete":
                    System.out.print("Enter index to delete: ");
                    int index = Integer.parseInt(scanner.nextLine());
                    manager.deleteExpense(index);
                    break;

                case "summary":
                    manager.summarizeExpenses();
                    break;

                case "exit":
                    System.out.println("Exiting the tracker. Goodbye!");
                    break;

                default:
                    System.out.println("Invalid command.");
            }
        } while (!command.equals("exit"));

        scanner.close();
    }
}
