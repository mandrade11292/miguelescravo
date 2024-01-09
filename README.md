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
