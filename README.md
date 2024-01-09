# miguelescravo
trabalho de escravos
 using System;
 


using System.Collections.Generic;

using System.ComponentModel;

using System.Data;

using System.Drawing;

using System.Linq;

using System.Text;

using System.Threading.Tasks;

using System.Windows.Forms;

using System.IO;



namespace teste_do_trabalho_escravo

{
    public partial class Form1 : Form
    {
        private Button[] botoes;
        public Form1()
        {
            InitializeComponent();
            InicializarBotoes();
        }
        private void InicializarBotoes()
        {
            // Assumindo que você já possui botões chamados btn_1, btn_2, ..., btn_40
            botoes = new Button[40];

            for (int i = 0; i < 40; i++)
            {
                Control[] foundControls = Controls.Find($"btn_{i + 1}", true);

                // Verifica se há controles com o nome especificado e se a matriz é não nula
                if (foundControls != null && foundControls.Length > 0 && foundControls[0] is Button)
                {
                    botoes[i] = (Button)foundControls[0];
                    botoes[i].Click += (sender, e) => AbrirFormEdit((Button)sender);
                }
                else
                {
                    // Lida com a situação em que o controle não é encontrado
                    MessageBox.Show($"Botão btn_{i + 1} não encontrado.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
                }
            }
        }
        private void AbrirFormEdit(Button botao)
        {
            using (edit edit = new edit())
            {
                if (edit.ShowDialog() == DialogResult.OK)
                {
                    string disciplinaSelecionada = edit.DisciplinaSelecionada;
                    string caminhoArquivo = $"{botao.Name}.txt";

                    File.WriteAllText(caminhoArquivo, disciplinaSelecionada);
                    botao.Text = disciplinaSelecionada;
                }
            }
        }

    }
}



using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.IO;

namespace teste_do_trabalho_escravo
{
    public partial class edit : Form
    {
        private ComboBox cmbDisciplinas;
        private Button btnSalvar;

        public string DisciplinaSelecionada { get; private set; }

        public edit()
        {
            InitializeComponent();
        }
        private void InicializarComponentes()
        {
            cmbDisciplinas = new ComboBox();
            btnSalvar = new Button();

            cmbDisciplinas.Items.AddRange(new object[] { "Matemática", "Português", "Ciências", "História", "Geografia", "Inglês", "Arte", "Educação Física", "Biologia", "Química", "Física", "Filosofia" });

            btnSalvar.Text = "Salvar";
            btnSalvar.Click += (sender, e) => SalvarDisciplina();

            Controls.Add(cmbDisciplinas);
            Controls.Add(btnSalvar);
        }

        private void SalvarDisciplina()
        {
            DisciplinaSelecionada = cmbDisciplinas.SelectedItem?.ToString();
            DialogResult = DialogResult.OK;
            Close();
        }
        private void button1_Click(object sender, EventArgs e)
        {
       
        }
        private void InicializarBotoes()
{
    // Assumindo que você já possui botões chamados btn_1, btn_2, ..., btn_40
    botoes = new Button[40];

    for (int i = 0; i < 40; i++)
    {
        Control[] foundControls = Controls.Find($"btn_{i + 1}", true);

        // Verifica se há controles com o nome especificado e se a matriz é não nula
        if (foundControls != null && foundControls.Length > 0 && foundControls[0] is Button)
        {
            botoes[i] = (Button)foundControls[0];
            botoes[i].Click += (sender, e) => AbrirFormEdit((Button)sender);
        }
        else
        {
            // Lida com a situação em que o controle não é encontrado
            MessageBox.Show($"Botão btn_{i + 1} não encontrado.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
        }
    }
}
 InicializarBotoes();
 private Button[] botoes;
    }
}



