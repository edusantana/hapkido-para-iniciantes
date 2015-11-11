desc "Gera epubs do livro"
task :epub

EPUB = "hapkido-para-iniciantes.epub"


file EPUB => ["exame-de-faixa.md", "regras-etiquena-no-dojang.md", "metadata.yaml"] do
  system "pandoc -S exame-de-faixa.md regras-etiquena-no-dojang.md metadata.yaml -o hapkido-para-iniciantes.epub"
end

task :clean do
  rm EPUB
end

task :epub => EPUB

task :default => [:clean, EPUB]
