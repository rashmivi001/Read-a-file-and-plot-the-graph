# Read-a-file-and count number of particular word occurring in a line and then-plot-the-graph for those values
#Java Program

package com.filereader;

import java.awt.Rectangle;
import java.io.*;
import javax.swing.JFrame;

import org.knowm.xchart.QuickChart;
import org.knowm.xchart.SwingWrapper;
import org.knowm.xchart.XYChart;
import org.knowm.xchart.XYChartBuilder;
import org.knowm.xchart.style.Styler.LegendPosition;

public class FileProgram {

	public static void main(String[] args) throws IOException
	{
  File f=new File("D:\\Rashmi\\abc0206.txt");
  FileReader fr=new FileReader(f);
		BufferedReader br = new BufferedReader(fr);
		
		String s;
		String input="Java";
		double count=0.0; int line=0;  int j=0;
		double[] temp=new double[5];  
    
    while((s=br.readLine())!=null)   //Reading Content from the file
	  {
	     String[] words=s.split(" ");  
	     for (String word : words) 
	     {
	        if (word.equals(input))   
	        {
	          count++;  
	                
	        }
	                
	     }
       temp[j]=count;
	     j++; 
       
	     if(count!=0)  
		   {
		      System.out.println("The given word is present "+count+ " times in the line" +line);
		   }
		   else
		   {
		      System.out.println("The given word is not present in the file");
		   }
	     line++;
		   count=0;
	  }
    //  Chart Series graph
		    XYChart chart = new XYChartBuilder().width(800).height(600).title("AreaChart").xAxisTitle("X").yAxisTitle("Y").build();
	  //  System.out.println("J in chart" +temp[0]+ " " +temp[1]+ " "+temp[2]+ " " +temp[3]+ " " +temp[4]);
		    chart.addSeries("a",temp);   
		    new SwingWrapper(chart).displayChart();			 
	}	
}
