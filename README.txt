CHOOSE EVERYTHING! — V3.1 (ANIME IMAGES)
=========================================

NOVIDADES DESTA VERSÃO
- Todos os 100 cards da categoria Anime possuem mapeamento de imagem específico por personagem.
- Tanjiro usa a imagem local enviada pelo usuário: public/assets/tanjiro.png.
- Para os outros personagens de anime, o servidor tenta, nesta ordem:
  1) Jikan / MyAnimeList
  2) AniList
  3) Kitsu
  4) Wikipedia/Wikimedia
- Cada personagem usa um nome canônico próprio para evitar que formas como Ultra Instinct, Gear 5 e GER procurem a pessoa errada.
- As imagens remotas são repassadas pelo próprio servidor para reduzir imagens quebradas por hotlink.
- Se todos os provedores estiverem temporariamente indisponíveis, aparece um fallback visual em vez de uma imagem quebrada.
- O endpoint /api/health mostra animeImageMappings: 100.

MANTIDO DA V3
- 1.500 cartas no total.
- Botão COBRIR +1.
- Botão PASSAR.
- Modos 1v1, 1v1v1, 1v1v1v1, 2v2 e 3v3.
- Leilão por rodadas, sons, salas online e juiz final por IA quando OPENAI_API_KEY estiver configurada.
- O juiz agora é instruído a respeitar a forma/transformação escrita no nome da carta.

ATUALIZAR O RAILWAY
1. Extraia este ZIP.
2. No GitHub, substitua os arquivos do repositório pelos desta versão:
   - server.js
   - cards.json
   - anime-images.json
   - package.json
   - README.txt
   - pasta public/ inteira
3. Faça Commit changes.
4. O Railway deve redeployar automaticamente.

IMPORTANTE SOBRE AS FOTOS
O Tanjiro está embutido no pacote. Os outros 99 personagens de anime têm mapeamento individual,
mas a foto é obtida em tempo de execução de bases públicas. Se uma dessas bases ficar fora do ar,
o jogo tenta as próximas automaticamente.


V3.3 - AJUSTES DE LEILÃO E IMAGENS
-----------------------------------
- Poder/score removido completamente da interface e dos dados enviados ao navegador.
- Rodadas agora são digitáveis: 1 a 500.
- Moedas iniciais agora são digitáveis: 1 a 1.000.000.000.
- Cronômetro inicial: 10 segundos.
- TODO lance válido (inclusive Cobrir +1) reinicia o cronômetro para 10 segundos.
- O líder atual não pode clicar em Passar nem Cobrir a si próprio.
- Imagens são pré-carregadas no servidor antes do cronômetro começar.
- Próxima imagem é preparada em segundo plano durante a rodada atual.
- Bytes das imagens ficam em cache na memória para evitar novas buscas/downloads durante a sessão.
- Layout de fotos usa object-fit: contain para não cortar rostos/personagens.
- Tela de preparação aparece enquanto uma foto ainda está sendo resolvida.


V3.3
- cartão principal da rodada redesenhado para remover o “quadrado preto” em volta da imagem
- imagem principal agora fica destacada sem a caixa escura pesada ao redor
- nome continua abaixo da foto, em visual mais limpo


V3.4 — JUIZ CANÔNICO + IMAGEM LUCIUS
- O juiz de IA agora usa a forma exata quando a carta traz uma transformação.
- Quando a carta traz somente o nome do personagem, usa a versão canônica mais forte da fonte principal.
- Rimuru Tempest recebe orientação explícita para usar o auge canônico da light novel, não a versão inicial do anime.
- Adicionadas notas privadas de matchup para vários personagens de alto nível; elas não aparecem para os jogadores.
- Fallback local corrigido para não subestimar Rimuru/Anos/Yhwach/GER e outros high tiers.
- Lucius Zogratis agora evita o fallback genérico da Wikipedia e prioriza fontes de banco de anime para impedir a foto errada mostrada anteriormente.
- Busca automática de anime passa a priorizar AniList e rejeita matches muito fracos no Jikan/Kitsu.


V3.5 — CLASSIFICAÇÃO FINAL
- A IA agora retorna uma classificação completa de todos os times.
- Modos 1v1v1 e 1v1v1v1 mostram 1º, 2º, 3º e 4º.
- Modos 1v1, 2v2 e 3v3 mostram 1º e 2º.
- O juiz local também gera a classificação completa caso a API de IA falhe.
- A tela de resultado mostra pódio/classificação antes das cartas de cada time.


V3.6 — FACE PORTRAITS
- Melhorei a busca na internet para imagens de anime, priorizando APIs de personagens (AniList, Jikan e Kitsu).
- A busca agora tenta acertar melhor o nome do personagem antes de aceitar a imagem.
- As cartas de anime agora mostram retratos mais focados no rosto/parte superior do personagem.
- Miniaturas e tela principal usam crop de retrato para reduzir fotos bugadas ou com enquadramento ruim.
- /api/health agora mostra judgeVersion = 3.6-face-portraits


V3.7 — FORM PHOTOS + 150 ANIME
- Adicionados +50 personagens na categoria Anime (agora são 150 no total).
- Todas as 150 cartas de anime têm mapeamento de imagem.
- Para personagens com forma específica, a busca prioriza a forma correta:
  ex.: Goku Ultra Instinct, Vegeta Ultra Ego, Gear 5, Beast, Rosé, Blue, etc.
- Para essas cartas de forma, a ordem de busca passa a priorizar resultados específicos da forma.
- /api/health agora mostra judgeVersion = 3.7-form-photos-150-anime


V3.8 — CANON LOCKS
- Adicionado canon-locks.json com regras determinísticas para evitar resultados canônicos absurdos.
- A IA continua julgando matchups normais, mas não pode violar travas configuradas.
- Exemplo: em confronto direto aplicável, Zeno fica acima de Goku Ultra Instinct e dos lutadores de Dragon Ball listados.
- Também há travas conservadoras para Black Frieza > Goku UI/Vegeta UE, Whis > Beerus e mortais DB listados, Saitama > Cosmic Garou/Boros e Yoriichi > demônios listados.
- As travas só são aplicadas quando o time adversário inteiro está dentro da lista explícita da regra; isso evita decidir automaticamente cross-verse como Rimuru vs Zeno.
- Se uma trava corrigir a IA, a tela mostra "IA OpenAI + trava canônica".
- Para adicionar/remover regras, edite canon-locks.json.
- /api/health mostra judgeVersion = 3.8-canon-locks e canonLocks = quantidade de regras.


V3.9 — STRICT IMAGES + EXCLUIR SALA + POWER FINAL
- Corrigida a causa das fotos absurdamente erradas: cartas de Anime NÃO usam mais busca genérica/Wikipedia.
- Cada uma das 150 cartas de Anime agora possui metadados próprios: personagem-base, franquia, domínio da wiki correta e forma/transformação quando aplicável.
- Formas específicas tentam localizar arquivos/imagens da transformação dentro da wiki da PRÓPRIA franquia.
- AniList é usado como fallback validando o personagem e a obra; Jikan é um fallback conservador.
- Se nenhuma foto puder ser validada, o site mostra placeholder em vez de exibir uma pessoa/personagem errado.
- Adicionado cache busting IMAGE_CACHE_VERSION=anime-strict-v39 e removido cache immutable de 7 dias. Isso impede que uma foto errada antiga continue presa no navegador após deploy.
- Novo endpoint /api/image-debug/:id mostra a fonte/confiança da imagem para diagnóstico.
- Foto principal reduzida para ~360x360 no desktop e ~280x280 no celular, com crop de rosto/parte superior para Anime.
- Miniaturas reduzidas para 96x96 (84x84 no celular).
- Botão “🗑️ Excluir sala” no lobby, visível apenas para o host; backend também valida o host, encerra timers, avisa os jogadores e remove a sala.
- Power continua escondido durante o leilão e é revelado SOMENTE na tela final, ao lado da foto de cada carta/personagem.
- Anime usa uma escala de Power aproximada de 0–1000, aproveitando overrides privados de high tiers e os scores internos.
- /api/health: judgeVersion=3.9-strict-images-delete-power, imageVersion=anime-strict-v39.

- Regra extra de segurança: carta com forma/transformação NÃO cai para retrato-base. Se a forma exata não for validada, aparece placeholder com o nome em vez de uma forma errada.
