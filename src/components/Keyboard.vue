<template>
  <div class="row justify-content-start">
    <div
      v-for="char in alphabet"
      :key="char.charCodeAt(0)"
      class="col-2 col-lg-1"
      @click="clicked(char)"
    >
      <button class="character col-12" :id="'keyboard-' + char">
        {{ char }}
      </button>
    </div>
    <button class="Backspace character col-3 col-lg-2" @click="deleted()">
      &#8676;
    </button>
    <button class="Enter character col-4 col-lg-3" @click="enter()">
      Enter
    </button>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  setup() {
    let words = ['aback', 'abase', 'abate', 'abaya', 'abbey', 'abbot', 'abets', 'abhor', 'abide', 'abode', 'abort', 'about', 'above', 'abuse', 'abuts', 'abyss', 'ached', 'aches', 
'acids', 'acing', 'ackee', 'acorn', 'acres', 'acrid', 'acted', 'actin', 'actor', 'acute', 'adage', 'adapt', 'added', 'adder', 'addle', 'adept', 'adieu', 'adios', 'adits', 'adman', 'admin', 'admit', 'adobe', 'adobo', 'adopt', 'adore', 'adorn', 'adult', 'adzes', 'aegis', 'aeons', 'aerie', 'affix', 'afire', 'afoot', 'afore', 'after', 'again', 'agape', 'agate', 'agave', 'agent', 'aggro', 'agile', 'aging', 'aglow', 'agony', 'agora', 'agree', 'ahead', 'ahold', 'aided', 'aider', 'aides', 'ailed', 'aimed', 'aimer', 'aioli', 'aired', 'aisle', 'alarm', 'album', 'alder', 'aleph', 'alert', 'algae', 'algal', 'alias', 'alibi', 'alien', 'align', 'alike', 'alive', 'alkyd', 'alkyl', 'allay', 'alley', 'allot', 'allow', 'alloy', 'allyl', 'aloes', 'aloft', 'aloha', 'alone', 'along', 'aloof', 'aloud', 'alpha', 'altar', 'alter', 'altos', 'alums', 'amass', 'amaze', 'amber', 'ambit', 'amble', 'ambos', 'amend', 'amide', 'amine', 'amino', 'amiss', 'amity', 'amnio', 'among', 'amour', 'amped', 'ample', 'amply', 'amuse', 'ancho', 'angel', 'anger', 'angle', 'angry', 'angst', 'anima', 'anime', 'anion', 'anise', 'ankle', 'annas', 'annex', 'annoy', 'annul', 'anode', 'anole', 'antic', 'antis', 'antsy', 'anvil', 'aorta', 'apace', 'apart', 'aphid', 'apnea', 'apple', 'apply', 'apron', 'apses', 'apter', 'aptly', 'aquas', 'arbor', 'ardor', 'areal', 'areas', 'areca', 'arena', 'argon', 'argot', 'argue', 'argus', 'arias', 'arils', 'arise', 'armed', 'armor', 'aroma', 'arose', 'array', 
'arrow', 'arses', 'arson', 'artsy', 'asana', 'ascot', 'ashen', 'ashes', 'aside', 'asked', 'asker', 'askew', 'aspen', 'aspic', 'assay', 'asses', 'asset', 'aster', 'astir', 'asura', 'atlas', 'atman', 'atoll', 'atoms', 'atone', 'atopy', 'attic', 'audio', 'audit', 'auger', 'aught', 'augur', 'aunts', 'aunty', 'aural', 'auras', 'autos', 'auxin', 'avail', 'avers', 'avert', 'avian', 'avoid', 'avows', 'await', 'awake', 'award', 'aware', 'awash', 'awful', 'awoke', 'axels', 'axial', 'axils', 'axing', 'axiom', 'axion', 'axles', 'axons', 'azide', 'azole', 'azure', 'babel', 'babes', 'babka', 'backs', 'bacon', 'baddy', 'badge', 'badly', 'bagel', 'baggy', 'bails', 'bairn', 'baits', 'baize', 'baked', 'baker', 'bakes', 'baldy', 'baled', 'baler', 'bales', 'balks', 'balky', 'balls', 'balms', 'balmy', 'balsa', 'banal', 'bands', 'bandy', 'banes', 'bangs', 'banjo', 'banks', 'barbs', 'bards', 'bared', 'barer', 'bares', 'barge', 'barks', 'barmy', 'barns', 'baron', 'barre', 'basal', 'based', 'baser', 'bases', 'basic', 'basil', 'basin', 'basis', 'basks', 'basso', 'bassy', 'baste', 'batch', 'bated', 'bathe', 'baths', 'batik', 'baton', 'batts', 'batty', 'bawdy', 'bawls', 'bayed', 'bayou', 'beach', 'beads', 'beady', 'beaks', 'beams', 'beamy', 'beans', 'beard', 'bears', 'beast', 'beats', 'beaus', 'beaut', 'beaux', 'bebop', 'becks', 'beech', 'beefs', 'beefy', 'beeps', 'beers', 'beery', 'beets', 'befit', 'began', 'beget', 'begin', 'begun', 'beige', 'being', 'belay', 'belch', 
'belie', 'belle', 'bells', 'belly', 'below', 'belts', 'bench', 'bends', 'bread', 'bendy', 'bento', 'bents', 'beret', 'bergs', 'berms', 'berry', 'berth', 'beryl', 'beset', 'bests', 'betas', 'betel', 'betta', 'bevel', 'bezel', 'bhaji', 'bible', 'bicep', 'biddy', 'bided', 'bides', 'bidet', 'bight', 'bigot', 'bijou', 'biked', 'biker', 'bikes', 'biles', 'bilge', 'bills', 'billy', 'bimbo', 'bindi', 'binds', 'binge', 'bingo', 'biome', 'biota', 'bipod', 'birch', 'birds', 'birth', 'bison', 'bitch', 'biter', 'bites', 'bitsy', 'bitty', 'black', 'blade', 'blame', 'bland', 'blank', 'blare', 'blase', 'blast', 'blaze', 'bleak', 'bleat', 'blebs', 'bleed', 'bleep', 'blend', 'bless', 'blimp', 'blind', 'bling', 'blini', 'blink', 'blips', 'bliss', 'blitz', 'bloat', 'blobs', 'block', 'blocs', 'blogs', 'bloke', 'blond', 'blood', 'bloom', 'bloop', 'blots', 'blown', 'blows', 'blued', 'blues', 'bluey', 'bluff', 'blunt', 'blurb', 'blurs', 'blurt', 'blush', 'board', 'boars', 'boast', 'boats', 'bobby', 'bocce', 'boche', 'boded', 'bodes', 'boffo', 'bogey', 'boggy', 'bogie', 'bogus', 'boils', 'bolas', 'boles', 'bolls', 'bolts', 'bolus', 'bombe', 'bombs', 'bonds', 'boned', 'boner', 'bones', 'boney', 'bongo', 'bongs', 'bonks', 'bonny', 'bonus', 'boobs', 'booby', 'booed', 'books', 'booms', 'boomy', 'boons', 'boors', 'boost', 'booth', 'boots', 'booty', 'booze', 'boozy', 'boppy', 'borax', 'bored', 'borer', 'bores', 'boric', 'borne', 'boron', 'bosom', 'boson', 'bossy', 'bosun', 'botch', 
'bough', 'boule', 'bound', 'bouts', 'bowed', 'bowel', 'bower', 'bowls', 'boxed', 'boxer', 'boxes', 'boyar', 'boyos', 'bozos', 'brace', 'bract', 'brads', 'brags', 'braid', 'brain', 'brake', 'brand', 'brans', 'brash', 'brass', 'brats', 'brave', 'bravo', 'brawl', 'brawn', 'brays', 'braze', 'bread', 'break', 'bream', 'breed', 'brews', 'briar', 'bribe', 'brick', 'bride', 'brief', 'brier', 'brigs', 'brims', 'brine', 'bring', 'brink', 'briny', 'brisk', 'brits', 'broad', 'broch', 'broil', 'broke', 'brome', 'bronc', 'brood', 'brook', 'broom', 'broth', 'brown', 'brows', 'bruin', 'bruit', 'brunt', 'brush', 'brute', 'bubba', 'bucks', 'buddy', 'budge', 'buffs', 'buggy', 'bugle', 'build', 'built', 'bulbs', 'bulge', 'bulks', 'bulky', 'bulla', 'bulls', 'bully', 'bumps', 'bumpy', 'bunch', 'bunds', 'bundt', 'bunks', 'bunny', 'bunts', 'buoys', 'burbs', 'burgs', 'burka', 'burly', 'burns', 'burnt', 'burps', 'burqa', 'burro', 'burrs', 'bursa', 'burst', 'bused', 'buses', 'bushy', 'busts', 'busty', 'butch', 'butte', 'butts', 'buxom', 'buyer', 'buzzy', 'bylaw', 'byres', 'bytes', 'byway', 'cabal', 'cabby', 'caber', 'cabin', 'cable', 'cacao', 'cache', 'cacti', 'caddy', 'cadet', 'cadre', 'cafes', 'caged', 'cages', 'cagey', 'cairn', 'caked', 'cakes', 'cakey', 'calfs', 'calif', 'calla', 'calls', 'calms', 'calve', 'calyx', 'camel', 'cameo', 'campo', 'camps', 'campy', 'canal', 'candy', 'caned', 'canes', 'canid', 'canna', 'canny', 'canoe', 'canon', 'canto', 'caped', 'caper', 
'capes', 'capon', 'capos', 'caput', 'carat', 'carbo', 'carbs', 'cards', 'cared', 'carer', 'cares', 'cargo', 'carob', 'carol', 'carom', 'carps', 'carry', 'carte', 'carts', 'carve', 'cased', 'cases', 'casks', 'caste', 'casts', 'catch', 'cater', 'catty', 'caulk', 'cause', 'caved', 'caver', 'caves', 'cavil', 'cease', 'cecal', 'cecum', 'cedar', 'ceded', 'cedes', 'ceili', 'celeb', 'cello', 'cells', 'celts', 'cents', 'chads', 'chafe', 'chaff', 'chain', 'chair', 'chalk', 'champ', 'chana', 'chant', 'chaos', 'chaps', 'chard', 'charm', 'chars', 'chart', 'chase', 'chasm', 'chats', 'cheap', 'cheat', 'check', 'cheek', 'cheep', 'cheer', 'chefs', 'chemo', 'chert', 'chess', 'chest', 'chews', 'chewy', 'chica', 'chick', 'chico', 'chide', 'chief', 'child', 'chile', 'chili', 'chill', 'chime', 'chimp', 'china', 'chine', 'ching', 'chino', 'chins', 'chips', 'chirp', 'chits', 'chive', 'chock', 'choir', 'choke', 'chomp', 'chops', 'chord', 'chore', 'chose', 'chows', 'chubs', 'chuck', 'chuff', 'chugs', 'chump', 'chums', 'chunk', 'churn', 'chute', 'cider', 'cigar', 'cinch', 'circa', 'cisco', 'cited', 'cites', 'civet', 'civic', 'civil', 'civvy', 'clack', 'clade', 'claim', 'clamp', 'clams', 'clang', 'clank', 'clans', 'claps', 'clash', 'clasp', 'class', 'clave', 'claws', 'clays', 'clean', 'clear', 'cleat', 'clefs', 'cleft', 'clerk', 'click', 'cliff', 'climb', 'clime', 'cline', 'cling', 'clink', 'clips', 'cloak', 'clock', 'clods', 'clogs', 'clomp', 'clone', 'close', 'cloth', 
'clots', 'cloud', 'clout', 'clove', 'clown', 'clubs', 'cluck', 'clued', 'clues', 'clump', 'clung', 'clunk', 'coach', 'coals', 'coast', 'coati', 'coats', 'cobia', 'cobra', 'cocci', 'cocks', 'cocky', 'cocoa', 'codas', 'codec', 'coded', 'coder', 'codes', 'codex', 'codon', 'coeds', 'cohos', 'coifs', 'coils', 'coins', 'cokes', 'colas', 'colds', 'coles', 'colic', 'colin', 'colon', 'color', 'colts', 'comas', 'combo', 'combs', 'comer', 'comes', 'comet', 'comfy', 'comic', 'comma', 'commo', 'compo', 'comps', 'comte', 'conch', 'condo', 'coned', 'cones', 'conga', 'congo', 'conic', 'conks', 'cooed', 'cooks', 'cools', 'coops', 'coopt', 'coped', 'copes', 'copra', 'copse', 'coral', 'cords', 'cored', 'corer', 'cores', 'corgi', 'corks', 'corky', 'corms', 'corns', 'cornu', 'corny', 'corps', 'costs', 'cotta', 'couch', 'cough', 'could', 'count', 'coupe', 'coups', 'court', 'coven', 'cover', 'coves', 'covet', 'covey', 'cowed', 'cower', 'cowls', 'coyly', 'crabs', 'crack', 'craft', 'crags', 'cramp', 'crams', 'crane', 'crank', 'crape', 'craps', 'crash', 'crass', 'crate', 'crave', 'crawl', 'craws', 'craze', 'crazy', 'creak', 'cream', 'credo', 'creed', 'creek', 'creel', 'creep', 'creme', 'crepe', 'crept', 'cress', 'crest', 'crews', 'cribs', 'crick', 'cried', 'crier', 'cries', 'crime', 'crimp', 'crisp', 'crits', 'croak', 'crock', 'crocs', 'croft', 'crone', 'crony', 'crook', 'croon', 'crops', 'cross', 'croup', 'crowd', 'crown', 'crows', 'crude', 'cruel', 'cruet', 'crumb', 
'cruse', 'crush', 'crust', 'crypt', 'cubby', 'cubed', 'cubes', 'cubic', 'cubit', 'cuddy', 'cuffs', 'culls', 'culpa', 'cults', 'cumin', 'cupid', 'cuppa', 'curbs', 'curds', 'cured', 'cures', 'curia', 'curio', 'curls', 'curly', 'curry', 'curse', 'curve', 'curvy', 'cushy', 'cusps', 'cuter', 'cutie', 'cutis', 'cutup', 'cycad', 'cycle', 'cyclo', 'cynic', 'cysts', 'czars', 'dacha', 'daddy', 'dados', 'daffy', 'daily', 'dairy', 'daisy', 'dales', 'dames', 'damns', 'damps', 'dance', 'dandy', 'dared', 'dares', 'darks', 'darns', 'darts', 'dashi', 'dated', 'dater', 'dates', 'datum', 'daubs', 'daunt', 'davit', 'dawns', 'dazed', 'deals', 'dealt', 'deans', 'dears', 'deary', 'death', 'debit', 'debts', 'debug', 'debut', 'decaf', 'decal', 'decay', 'decks', 'decor', 'decoy', 'decry', 'deeds', 'deems', 'deeps', 'deers', 'defer', 'deify', 'deign', 'deism', 'deist', 'deity', 'dekes', 'delay', 'delft', 'delis', 'dells', 'delta', 'delve', 'demon', 'demos', 'demur', 'denim', 'dense', 'dents', 'depot', 'depth', 'derby', 'desks', 'deter', 'detox', 'deuce', 'devil', 'dewar', 'dhikr', 'dhows', 'dials', 'diary', 'diced', 'dices', 'dicey', 'dicky', 'dicta', 'diets', 'digit', 'diked', 'dikes', 'dills', 'dilly', 'dimer', 'dimes', 'dimly', 'dinar', 'dined', 'diner', 'dines', 'dingo', 'dings', 'dingy', 'dinks', 'dinky', 'dinos', 'diode', 'dippy', 'direr', 'dirge', 'dirty', 'disco', 'discs', 'dishy', 'disks', 'ditch', 'ditsy', 'ditto', 'ditty', 'ditzy', 'divan', 'divas', 'dived', 
'diver', 'dives', 'divot', 'divvy', 'dizzy', 'docks', 'dodge', 'dodgy', 'dodos', 'doers', 'doffs', 'doges', 'doggy', 'dogma', 'doing', 'doled', 'doles', 'dolls', 'dolly', 'dolor', 'dolts', 'domed', 'domes', 'donee', 'dongs', 'donna', 'donor', 'donut', 'dooms', 'doomy', 'doors', 'doozy', 'doped', 'dopes', 'dopey', 'dorks', 'dorky', 'dorms', 'dosas', 'dosed', 'doses', 'doted', 'dotes', 'dotty', 'doubt', 'dough', 'doula', 'douse', 'doves', 'dowdy', 'dowel', 'dower', 'downs', 'downy', 'dowry', 'dowse', 'doyen', 'dozed', 'dozen', 'dozer', 'dozes', 'drabs', 'draft', 'drags', 'drain', 'drake', 'drama', 'drams', 'drank', 'drape', 'drawl', 'drawn', 'draws', 'drays', 'dread', 'dream', 'dreck', 'dregs', 'dress', 'dribs', 'dried', 'drier', 'dries', 'drift', 'drill', 'drily', 'drink', 'drips', 'drive'];
    let word = words[Math.floor(Math.random() * words.length)];
    word = word.toUpperCase();
    let choosen = 0;
    let word_count = 1;
    const alphabet = ref([
      "Q",
      "W",
      "E",
      "R",
      "T",
      "Y",
      "U",
      "I",
      "O",
      "P",
      "A",
      "S",
      "D",
      "F",
      "G",
      "H",
      "J",
      "K",
      "L",
      "Z",
      "X",
      "C",
      "V",
      "B",
      "N",
      "M",
    ]);
    /* eslint-disable */
    function clicked(e) {
      if (choosen <= 4) {
        document.getElementById(`word${word_count}-${choosen + 1}`).innerHTML =
          e;
        choosen += 1;
      }
    }
    function deleted() {
      if (choosen > 0) {
        document.getElementById(`word${word_count}-${choosen}`).innerHTML = "";

        choosen -= 1;
      }
    }
    function enter() {
      let corrects = 0;
      if (choosen == 5 && word_count<=6) {
          let choosen_word = ""
          for (let i=1;i<=5;i++){
            
                  choosen_word+=document.getElementById(
                      `word${word_count}-${i}`
          ).innerHTML.toLowerCase();

          }
          if(!words.includes(choosen_word)){
              alert("word not avalable")
              return
          }
        let miss_word = word;
        for (let i = 1; i <= 5; i++) {
          let character = document.getElementById(
            `word${word_count}-${i}`
          ).innerHTML;
          if (word[i - 1].toUpperCase() == character) {
            document.getElementById(`word${word_count}-${i}`).className +=
              " correct ";
            document.getElementById(`keyboard-${character}`).className +=
              " correct ";
            document.getElementById(`keyboard-${character}`).className =
              document
                .getElementById(`keyboard-${character}`)
                .className.replace("missplace", "");
            corrects++;
            miss_word = word.replace(character, "");
          } else if (miss_word.includes(character)) {
            if (
              document
                .getElementById(`keyboard-${character}`)
                .className.includes("correct") || document
                .getElementById(`keyboard-${character}`)
                .className.includes("missplace")
            ) {
              document.getElementById(`word${word_count}-${i}`).className +=
                " notfound ";
              continue;
            }

            miss_word = miss_word.replace(character, "");
            document.getElementById(`word${word_count}-${i}`).className +=
              " missplace ";
            document.getElementById(`keyboard-${character}`).className +=
              " missplace ";
            //document.getElementById(`keyboard-${character}`).className = document.getElementById(`keyboard-${character}`).classList["notfound"]
          } else {
            document.getElementById(`word${word_count}-${i}`).className +=
              " notfound ";
            document.getElementById(`keyboard-${character}`).className +=
              " notfound ";
          }
        }
        word_count += 1;
        choosen = 0;
      }
    }
    return { alphabet, clicked, choosen, deleted, enter };
  },
};
</script>

<style scoped>
.character {
  background-color: rgb(233, 233, 233);
  padding: 7px 0;
  margin-bottom: 8px;
  font-weight: 700;
  cursor: pointer;
  border: 1px rgb(102, 179, 226) solid;
  border-radius: 5px;
}
.Backspace {
  margin-right: 10px;
}
.correct {
  background-color: green !important;
}
.missplace {
  background-color: rgb(181, 148, 3);
}
.notfound {
  background-color: rgb(169, 169, 169);
}
</style>
