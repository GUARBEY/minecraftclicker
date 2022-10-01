# minecraftclicker
YouTube/Guarbey Kanalında Detaylı Anlatım Mevcuttur ! 



using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Runtime.InteropServices;

namespace clicker3
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }
        List<int> Interval= new List<int>();
        [DllImport("user32.dll")]
        static extern void mouse_event(int dwlags,int dx,int dy,int dwData,int dwExtraInfo);
        private const int MOUSEEVENTF_LEFTDOWN = 0x0002;
        private const int MOUSEEVENTF_LEFTUP = 0x0004;
        private void trackBar1_Scroll(object sender, EventArgs e)
        {
            label2.Text = $"CPS : {2 * trackBar1.Value}";
            if (trackBar1.Value == 0)
            {
                btn_start.Enabled = false;
                btn_bind.Enabled = false;
            }
            else
            {
                btn_start.Enabled = true;
                btn_bind.Enabled = true;
            }
        }

        private void trackBar1_MouseDown(object sender, MouseEventArgs e)
        {
            label2.Text = $"CPS : {2 * trackBar1.Value}";
            if (trackBar1.Value == 0)
            {
                btn_start.Enabled = false;
                btn_bind.Enabled = false;
            }
            else
            {
                btn_start.Enabled = true;
                btn_bind.Enabled = true;
            }
        }

        private void trackBar1_MouseMove(object sender, MouseEventArgs e)
        {
            label2.Text = $"CPS : {2 * trackBar1.Value}";
            if (trackBar1.Value == 0)
            {
                btn_start.Enabled = false;
                btn_bind.Enabled = false;
            }
            else
            {
                btn_start.Enabled = true;
                btn_bind.Enabled = true;
            }
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            btn_start.Enabled = false;
            btn_bind.Enabled = false;
            Interval.Add(400); //2
            Interval.Add(200); //4
            Interval.Add(150); //6
            Interval.Add(100); //8
            Interval.Add(90); //10
            Interval.Add(80); //12
            Interval.Add(71); //14
            Interval.Add(59); //16
            Interval.Add(49); //18
            Interval.Add(42); //20
        }

        private void btn_start_Click(object sender, EventArgs e)
        {
            if (btn_start.Text == "ENABLE")
            {
                btn_start.Text = "DİSABLE";
                trackBar1.Enabled = false;
                MessageBox.Show("5 Saniye içerisinde başlayacak", "Warning",MessageBoxButtons.OK,MessageBoxIcon.Warning);
                System.Threading.Thread.Sleep(5000);
                timer1.Interval = Interval[trackBar1.Value-1];
                timer1.Enabled = true;
            }
            else
            {
                btn_start.Text = "ENABLE";
                trackBar1.Enabled = true;
                timer1.Enabled= false;
            }
        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            mouse_event(MOUSEEVENTF_LEFTDOWN,Control.MousePosition.X, Control.MousePosition.Y,0,0);
            mouse_event(MOUSEEVENTF_LEFTUP, Control.MousePosition.X,Control.MousePosition.Y,0,0);
        }

        private void btn_bind_Click(object sender, EventArgs e)
        {
            btn_bind.Text = ". . .";
        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void Form1_Scroll(object sender, ScrollEventArgs e)
        {

        }

        private void radioButton1_CheckedChanged(object sender, EventArgs e)
        {
            BackColor = Color.Orange;
        }

        private void radioButton2_CheckedChanged(object sender, EventArgs e)
        {
            BackColor = Color.LightGreen;
        }

        private void radioButton3_CheckedChanged(object sender, EventArgs e)
        {
            BackColor = Color.Black;
        }

        private void button1_Click(object sender, EventArgs e)
        {
            Form2 form2 = new Form2();
            form2.ShowDialog();
            this.Hide();
        }
    }
}

