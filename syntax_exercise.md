EXERCISE

I. Create a grammar for a small language using BNF that accepts a program code

<code> -> begin <stmts> end
<stmts> -> <assign>; | <assign>; <stmts>
<assign> -> <id> = <expr>
<id> -> A | B | C
<expr> -> <id> + <expr> | <id> * <expr> | (expr) | <id>


II. Derive the statement below and create a parse tree for it
	begin B = C * A + B * B; C = (B * C + A); end

<code>  => begin <stmts> end
	=> begin <assign>; <stmts> end
	=> begin <id>=  <expr>; <stmts> end
	=> begin B = <expr>; <stmts> end
	=> begin B = <id> * <expr>; <stmts> end
	=> begin B = C * <expr>; <stmts> end
	=> begin B = C * <id> + <expr>; <stmts> end
	=> begin B = C * A + <expr>; <stmts> end
	=> begin B = C * A + <id> * <expr>; <stmts> end
	=> begin B = C * A + B * <expr>; <stmts> end
	=> begin B = C * A + B * <id>; <stmts> end
	=> begin B = C * A + B * B; <stmts> end
	=> begin B = C * A + B * B; <assign>; end
	=> begin B = C * A + B * B; <id> = <expr>; end
	=> begin B = C * A + B * B; C = <expr>; end
	=> begin B = C * A + B * B; C = (expr); end
	=> begin B = C * A + B * B; C = (<id> * <expr>); end
	=> begin B = C * A + B * B; C = (B * <expr>); end
	=> begin B = C * A + B * B; C = (B * <id> + <expr>); end
	=> begin B = C * A + B * B; C = (B * C + <expr>); end
	=> begin B = C * A + B * B; C = (B * C + <id>); end
	=> begin B = C * A + B * B; C = (B * C + A); end