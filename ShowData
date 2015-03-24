package com.servlet.java;

import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.json.simple.JSONArray;
import org.json.simple.JSONObject;


public class ShowData extends HttpServlet {
	private static final long serialVersionUID = 1L;
       Connection con;
 
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		PrintWriter out=response.getWriter();
		out.print(createJSON().toJSONString());
	
	}


	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		PrintWriter out=response.getWriter();
		out.print(createJSON().toJSONString());
	}
	
	private JSONObject createJSON() {
		// TODO Auto-generated method stub
		JSONObject jobj=new JSONObject();
		JSONArray arr=new JSONArray();
		try {
			Class.forName("com.mysql.jdbc.Driver");
			con=DriverManager.getConnection("jdbc:mysql://localhost:3306/android","root","");
			String query="select * from food";
			Statement st=con.createStatement();
			
			ResultSet set=st.executeQuery(query);
			
			while(set.next())
			{
				String foodid=set.getString("username");
				String foodname=set.getString("userpassword");
				
				JSONObject obj=new JSONObject();
				obj.put("id", foodid);
				obj.put("name", foodname);
				arr.add(obj);
			}
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		jobj.put("users", arr);
		return jobj;
	}
}
