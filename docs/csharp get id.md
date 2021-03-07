## Get Id of newly created record - C#, SQL

So you have database with Customers and your first column is a ID column which (is Identity) is set to YES. You want to create a new customer and retrieve the newly created customer ID to maybe insert in a differnt table eg. orders.

The following c# code snippet would help to accoumplish this:

* public string Create(string Name, string Address, string Contact, string Email)
        {
            string id = "";
            string query = "INSERT INTO Customers OUTPUT Inserted.Customer_Id VALUES(@Name, @Address, @Contact, @Email)";
            string constr = ConfigurationManager.ConnectionStrings["constr"].ConnectionString;
            using (SqlConnection con = new SqlConnection(constr))
            {
                using (SqlCommand cmd = new SqlCommand(query))
                {
                    cmd.Parameters.AddWithValue("@Name", Name);
                    cmd.Parameters.AddWithValue("@Address", Address);
                    cmd.Parameters.AddWithValue("@Contact", Contact);
                    cmd.Parameters.AddWithValue("@Email", Email);
                    cmd.Connection = con;
                    con.Open();
                    id = ((int)cmd.ExecuteScalar()).ToString();
                    con.Close();
                }
            }
                 
            DoWhatYouWantWith(id);
            return "Customer has been successfully created";
        }` 


Thank you

Trevor Ngogodo