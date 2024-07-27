# my-project
using System.Data.SqlClient;

namespace my_project
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            SqlConnection con = new SqlConnection("Data Source=LAPTOP-C7UGJHSC;Initial Catalog=cmblogin;Integrated Security=True");
            SqlCommand cmd = new SqlCommand("select * from login where username='" + txtuser.Text + "' and password= '" + txtpass.Text + "'", con);
            SqlDataAdapter sda = new SqlDataAdapter(cmd);
            DataTable dt = new DataTable();
            sda.Fill(dt);
            string cmbItemValue = comboBox1.SelectedItem.ToString();
            if(dt.Rows.Count > 0)
            {
                for (int i = 0; i < dt.Rows.Count; i++)
                {
                    if (dt.Rows[i]["usertype"].ToString() == cmbItemValue)
                    {
                        MessageBox.Show("you are login as" + dt.Rows[i][2]);
                        if(comboBox1.SelectedIndex == 0)
                        {
                            Form2 f = new Form2();
                            f.Show();
                            this.Hide();
                        }
                        else 
                        {
                            Form3 ff = new Form3();
                            ff.Show();
                            this.Hide();
                        }
                    }

                        
                }
                   
            }
            else
            {
                MessageBox.Show("error");
            }
        }
    }
}
