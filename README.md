package main;
import java.util.Scanner;

class Reward_Value{
	private double cashvalue;
	public double milesvalue;
	public static final double miles_conversion_rate =0.0035;
	
	public Reward_Value(double cashvalue){
		this.cashvalue=cashvalue;
		this.milesvalue = cashvalue / miles_conversion_rate;
    }
	public Reward_Value(int milesValue) {
        this.milesvalue = milesValue;
        this.cashvalue = milesValue * miles_conversion_rate;
    }
	public double getmilesvalue(){
		return milesvalue;
	}
	public double getcashvalue(){
		return cashvalue;
	}
	
	
}

public class RewardsConvertor {
    public static void main(String[] args) {
    	
        var scanner = new Scanner(System.in);
        System.out.println("Welcome to the Credit Card Rewards Converter!");
        System.out.println("Please enter a cash value to convert to airline miles: ");
        var input_value = scanner.nextLine();
        double cashValue;
        try {
            cashValue = Double.parseDouble(input_value);
        } catch (NumberFormatException exception) {
            System.out.println("Could not parse input value as a double, exiting");
            return;
        }
        System.out.println("Converting $" + input_value + " to miles");
        var rewardsValue = new Reward_Value(cashValue);
        System.out.println("$" + input_value + " is worth " + rewardsValue.getmilesvalue() + " miles");

        // Also convert miles to cash to demonstrate both constructors
        System.out.println("Please enter miles value to convert to cash: ");
        var milesInput = scanner.nextLine();
        int milesValue;
        try {
            milesValue = Integer.parseInt(milesInput);
        } catch (NumberFormatException exception) {
            System.out.println("Could not parse input value as an integer, exiting");
            return;
        }
        var milesRewardsValue = new Reward_Value(milesValue);
        System.out.println(milesValue + " miles are worth $" + milesRewardsValue.getcashvalue());
    }
}





