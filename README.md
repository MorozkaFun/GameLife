# public partial class Form1 : Form
    {
  
     
      public char[,] table = new char[20, 20];
      public char[,] table1 = new char[20, 20];
      public  Bitmap bitfield = new Bitmap(400, 400);
      public  Graphics gr;

      public  Random rand=new Random();
      public Form1()
      {
            
            InitializeComponent();
            Random ran = new Random();
            gr =  Graphics.FromImage(bitfield);

            gr.Clear(Color.Black);



            int t, i;
            int j, h;
      




            for (t = 0; t < 20; t++)
            {


                for (i = 0; i < 20; i++)
                {

                    table[t, i] = '/';
              




                }

             

            }
       

            for (int y = 0; y < 100; y++)
            {
                j = ran.Next(0, 19);
                h = ran.Next(0, 19);
                table[j, h] = 'X';

            }

      
        }
        public void Racshet()
        {
            for (int t = 0; t < table.GetLength(0); t++)
            {



                for (int i = 0; i < table.GetLength(1); i++)
                {


                    int life = 0; 
                      int  dead = 0;
                    if (table[t, ((i + 1 > table.GetLength(1) - 1) ? 0 : i + 1)] == 'X')
                    {
                        life++;
                    }
                    else
                    {
                        dead++;
                    }




                    if (table[(t + 1 > table.GetLength(0) - 1) ? 0 : t + 1, i + 1 > table.GetLength(1) - 1 ? 0 : i + 1] == 'X')
                    {
                        life++;
                    }
                    else
                    {
                        dead++;
                    }


                    if (table[t - 1 < 0 ? table.GetLength(0) - 1 : t - 1, i] == 'X')
                    {

                        life++;
                    }
                    else
                    {
                        dead++;
                    }







                    if (table[t - 1 < 0 ? table.GetLength(0) - 1 : t - 1, i - 1 < 0 ? table.GetLength(1) - 1 : i - 1] == 'X')
                    {
                        life++;
                    }
                    else
                    {
                        dead++;
                    }






                    if (table[t, i - 1 < 0 ? table.GetLength(1) - 1 : i - 1] == 'X')
                    {
                        life++;
                    }
                    else
                    {
                        dead++;
                    }




                    if (table[(t + 1 > table.GetLength(0) - 1) ? 0 : t + 1, i - 1 < 0 ? table.GetLength(1) - 1 : i - 1] == 'X')
                    {
                        life++;
                    }
                    else
                    {
                        dead++;
                    }



                    if (table[(t + 1 > table.GetLength(0) - 1) ? 0 : t + 1, i] == 'X')
                    {
                        life++;
                    }
                    else
                    {
                        dead++;
                    }

                    if (table[t - 1 < 0 ? table.GetLength(0) - 1 : t - 1, i + 1 > table.GetLength(1) - 1 ? 0 : i + 1] == 'X')
                    {
                        life++;
                    }
                    else
                    {
                        dead++;
                    }


                    if (((life == 3) & (table[t, i] == '/')))
                    {
                        table1[t, i] = 'X';



                    }
                    if (life < 2)
                    {
                        table1[t, i] = '/';
                    }
                    if (life > 3)
                    {
                        table1[t, i] = '/';
                    }
                    if ((life == 2) & (table[t, i] == 'X'))
                        
                    {
                        table[t, i] = 'X';
                    }
                    }
            }
            table = table1;

        }
        public void WatchXXX()
        {
            
            for (int t = 0; t < table.GetLength(0); t++)
            {


                for (int i = 0; i < table.GetLength(1); i++)
                {


                    if (table[t, i] == 'X')
                    {
                       
                        gr.FillRectangle(Brushes.Green,t*10, i * 10, 10, 10);
                    }
                    else
                    {
                 
                        gr.FillRectangle(Brushes.Black, t * 10, i * 10, 10, 10);
                    }
                }


            }
            pictureBox1.Image = bitfield;

        }


        private void button1_Click(object sender, EventArgs e)
        {

            Racshet();
            WatchXXX();

        }

        private void button2_Click(object sender, EventArgs e)
        {
 
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            WatchXXX();

            //pictureBox1.Image = bitfield;

        }
    }
    }
