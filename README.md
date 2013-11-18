First-Order Unification in Agda
===============================

Implementation of Conor McBride's [First-order unification by structural recursion](http://journals.cambridge.org/action/displayFulltext?type=1&fid=185140&jid=JFP&volumeId=13&issueId=06&aid=185139) in Agda.

I'm personally using this implement proof search in Agda, but should you wish to use it
directly you can do so as follows:

    -- provide a datatype for the symbols and define a decidable equality
    data Sym : ℕ → Set where
      ADD  : Sym 3
      SUC  : Sym 1
      ZERO : Sym 0

    decEqSym : ∀ {k} (f g : Sym k) → Dec (f ≡ g)
    decEqSym ADD  ADD  = yes refl
    decEqSym SUC  SUC  = yes refl
    decEqSym ZERO ZERO = yes refl
    
    -- import and open the unification module
    open import Unification Sym decEqSym

It uses version 0.7 of [the Agda "Standard Library"](http://wiki.portal.chalmers.se/agda/pmwiki.php?n=Libraries.StandardLibrary).
