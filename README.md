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
