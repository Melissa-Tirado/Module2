# Module2
Module 2 SDLC Assignment - CODE

package Module2LMS;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.Scanner;

public class LibraryManagementSystem {
public static void main(String[] args) {
        Catalog catalog = new Catalog();
        Scanner scanner = new Scanner(System.in);
        
        
        //start menu, user to select action

        while (true) {
            System.out.println("\nLibrary Management System");
            System.out.println("1. Add Book");
            System.out.println("2. Delete Book");
            System.out.println("3. Display Catalog");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // new line
            
            

            switch (choice) {
              
            	//program prompts user for book title and author
            	//scanner allows user to input book information
            	case 1:
                    System.out.print("Enter book title: ");
                    String title = scanner.nextLine();
                    System.out.print("Enter author name: ");
                    String author = scanner.nextLine();
                    catalog.addBook(title, author);
                    break;
                
                //program prompts user for ID of book to delete
                //scanner allows user to enter book ID to delete
                case 2:
                    System.out.print("Enter book ID to delete: ");
                    int idToDelete = scanner.nextInt();
                    catalog.deleteBook(idToDelete);
                    break;

                //display current catalog
                case 3:
                    catalog.displayCatalog();
                    break;
                
                //exit program
                case 4:
                    System.out.println("Exiting Library Management System.");
                    System.exit(0);

                //user error message
                default:
                    System.out.println("Please enter a valid option.");
            }
        }
    }
}


public class Book {

	    private int id;
	    private String title;
	    private String author;
	    
	    
	    //initialize book
	    public Book(int id, String title, String author) {
	        this.id = id;
	        this.title = title;
	        this.author = author;
	    }
	    
	    //get method for book ID
	    public int getId() {
	        return id;
	    }

	    //get method for book title
	    public String getTitle() {
	        return title;
	    }
	    
	    //get method for book author
	    public String getAuthor() {
	        return author;
	    }

	    //return string
	    public String toString() {
	        return "ID: " + id + ", Title: " + title + ", Author: " + author;
	    }
	}
	


package Module2LMS;

import java.util.ArrayList;
import java.util.Iterator;

public class Catalog {
	
		//array list to store books in catalog
	    private ArrayList<Book> books;

	    
	    //initialize catalog
	    public Catalog() {
	        books = new ArrayList<>();
	    }

	    //add new book to catalog
	    public void addBook(String title, String author) {
	        int id = books.size() + 1; // Generate ID
	        Book newBook = new Book(id, title, author); //create book entry
	        books.add(newBook); //add book to catalog
	        System.out.println("Book added successfully. ID assigned: " + id);
	    }
	    
	    
	    //delete book by ID
	    public void deleteBook(int id) {
	        Iterator<Book> iterator = books.iterator();
	        while (iterator.hasNext()) {
	            Book book = iterator.next();
	            if (book.getId() == id) {
	                iterator.remove();
	                System.out.println("Book with ID " + id + " deleted successfully.");
	                return;
	            }
	        }
	        System.out.println("Book with ID " + id + " not found.");
	    }

	    //display current catalog
	    public void displayCatalog() {
	        if (books.isEmpty()) {
	            System.out.println("Catalog is empty.");
	        } else {
	            System.out.println("Current Catalog:");
	            for (Book book : books) {
	                System.out.println(book);
	            }
	        }
	    }
	}

