/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package waitdemo;

import java.util.Scanner;
import java.util.logging.Level;
import java.util.logging.Logger;

/**
 *
 * @author abc
 */
public class Account {
    static int balance=1000;
    Thread t;
    public void deposit(int num){
        try {            
            wait();
            synchronized(Account.class){
                balance=balance+num;
                System.out.println("Deposited successfully");
               
            }
        } catch (InterruptedException ex) {
           ex.printStackTrace();
        }
    }
    public synchronized int withdraw(int num){
        try {
            Thread.sleep(1000);
            balance= balance-num;
            Thread.sleep(1000);
            notify();
        } catch (InterruptedException ex) {
           
        }
         return balance;
    }
    
    public static void main(String[] args) {
        Account a1= new Account();
        Thread t1=new Thread(new Runnable() {
            @Override
            public void run() {
                System.out.println("Enter the amount to be deposited");
                Scanner sc= new Scanner(System.in);
                int num= Integer.parseInt(sc.nextLine());
                a1.deposit(num);
            }
        });
        t1.start();
        
       Thread t2= new Thread(new Runnable() {
            @Override
            public void run() {
             System.out.println("Enter the amount to be withdraw");
                Scanner sc= new Scanner(System.in);
                int num= Integer.parseInt(sc.nextLine());
                a1.withdraw(num);
            }
        });
       t2.start();        
    }
}
rtutu
tykyok
tyiykjei7yk
rtsie76
tsjteiks
tyie67
styijie7ti
