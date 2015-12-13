import random

class Square():
	def __init__(self, row, col):
		self.row = row
		self.col = col
		self.piece = None
	
	def getRow(self):
		return self.row
		
	def getCol(self):
		return self.col
		
	def setPiece(self, piece):
		self.piece = piece
	
	def getPiece(self):
		return self.piece
		
	def getColor(self):
		''' Color: 1 = White, 0 = None, -1 = Black '''
		if self.getPiece() is None or not self.getPiece().isAlive():
			return 0
		return self.getPiece().getColor()

class Piece():
	def __init__(self, color, row, col):
		self.color = color
		self.row = row
		self.col = col
		self.type = None
		self.alive = True
	
	def getColor(self):
		return self.color * self.alive
		
	def setColor(self, val):
		self.color = val
		
	def getRow(self):
		return self.row
		
	def setRow(self, val):
		self.row = val
		
	def getCol(self):
		return self.col
		
	def setCol(self, val):
		self.col = val
	
	def getType(self):
		return self.type
		
	def setType(self, val):
		self.type = val
		
	def isAlive(self):
		return self.alive
		
	def setAlive(self, val):
		self.alive = val
	
	def possible_moves(self, board):
	  '''To be inherited'''
	
class Pawn(Piece):
	def __init__(self, color, row, col):
		Piece.__init__(self, color, row, col)
		self.type = 'P'
		self.promoted = False
		
	def getPromoted(self):
		return self.promoted
	
	def setPromoted(self, val):
		self.promoted = val
	
	def possible_moves(self, board):
		possible_moves = []
		if not self.isAlive():
			return possible_moves
		if self.getRow() == 3.5 + 3.5 * self.getColor():
			#TODO
			return possible_moves
		if board[(self.getRow() + self.getColor(), self.col)].getColor() == 0:
			#No piece on target square (one in front)
			possible_moves.append((self.getRow() + self.getColor(), self.getCol()))
		if self.getRow() == 3.5 - 2.5 * self.getColor():
			if board[(self.getRow() + self.getColor(), self.getCol())].getColor() == 0:
				#nothing in way one in front
				if board[(self.getRow() + 2*self.getColor(), self.getCol())].getColor() == 0:
					#nothing in way on target square (two in front)
					possible_moves.append((self.getRow() + 2 * self.getColor(), self.getCol()))
		if self.getCol() + 1 < 8:
			if board[(self.getRow() + self.getColor(), self.getCol() + 1)].getColor() == -self.getColor():
				possible_moves.append((self.getRow() + self.getColor(), self.getCol() + 1))
		if self.getCol() - 1 > -1:
			if board[(self.getRow() + self.getColor(), self.getCol() - 1)].getColor() == -self.getColor():
				possible_moves.append((self.getRow() + self.getColor(), self.getCol() - 1))
		return possible_moves
			#TODO: en passant
	
class Knight(Piece):
	def __init__(self, color, row, col):
		Piece.__init__(self, color, row, col)
		self.type = 'N'
    
	def possible_moves(self, board):
		possible_moves = []
		if not self.isAlive():
			return possible_moves
		if self.getRow() + 2 < 8 and self.getCol() + 1 < 8:
			if board[(self.getRow() + 2, self.getCol() + 1)].getColor() != self.getColor():
				possible_moves.append((self.getRow() + 2, self.getCol() + 1))
		if self.getRow() - 2 > -1 and self.getCol() + 1 < 8:
			if board[(self.getRow() - 2, self.getCol() + 1)].getColor() != self.getColor():
				possible_moves.append((self.getRow() - 2, self.getCol() + 1))
		if self.getRow() + 2 < 8 and self.getCol() - 1 > -1:
			if board[(self.getRow() + 2, self.getCol() - 1)].getColor() != self.getColor():
				possible_moves.append((self.getRow() + 2, self.getCol() - 1))
		if self.getRow() - 2 > -1 and self.getCol() - 1 > -1:
			if board[(self.getRow() - 2, self.getCol() - 1)].getColor() != self.getColor():
				possible_moves.append((self.getRow() - 2, self.getCol() - 1))
		if self.getRow() + 1 < 8 and self.getCol() + 2 < 8:
			if board[(self.getRow() + 1, self.getCol() + 2)].getColor() != self.getColor():
				possible_moves.append((self.getRow() + 1, self.getCol() + 2))
		if self.getRow() - 1 > -1 and self.getCol() + 2 < 8:
			if board[(self.getRow() - 1, self.getCol() + 2)].getColor() != self.getColor():
				possible_moves.append((self.getRow() - 1, self.getCol() + 2))
		if self.getRow() + 1 < 8 and self.getCol() - 2 > -1:
			if board[(self.getRow() + 1, self.getCol() - 2)].getColor() != self.getColor():
				possible_moves.append((self.getRow() + 1, self.getCol() - 2))
		if self.getRow() - 1 > -1 and self.getCol() - 2 > -1:
			if board[(self.getRow() - 1, self.getCol() - 2)].getColor() != self.getColor():
				possible_moves.append((self.getRow() - 1, self.getCol() - 2))
		return possible_moves

class Bishop(Piece):
	def __init__(self, color, row, col):
		Piece.__init__(self, color, row, col)
		self.type = 'B'
    
	def possible_moves(self, board):
		possible_moves = []
		if not self.isAlive():
			return possible_moves
		i = 1
		while self.getRow() + i < 8 and self.getCol() + i < 8 and board[(self.getRow() + i, self.getCol() + i)].getColor() == 0:
			possible_moves.append((self.getRow() + i, self.getCol() + i))
			i += 1
		if self.getRow() + i < 8 and self.getCol() + i < 8 and board[(self.getRow() + i, self.getCol() + i)].getColor() == -self.getColor():
			possible_moves.append((self.getRow() + i, self.getCol() + i))
		j = 1
		while self.getRow() - j > -1 and self.getCol() + j < 8 and board[(self.getRow() - j, self.getCol() + j)].getColor() == 0:
			possible_moves.append((self.getRow() - j, self.getCol() + j))
			j += 1
		if self.getRow() - j > -1 and self.getCol() + j < 8 and board[(self.getRow() - j, self.getCol() + j)].getColor() == -self.getColor():
			possible_moves.append((self.getRow() - j, self.getCol() + j))
		k = 1
		while self.getRow() + k < 8 and self.getCol() - k > -1 and board[(self.getRow() + k, self.getCol() - k)].getColor() == 0:
			possible_moves.append((self.getRow() + k, self.getCol() - k))
			k += 1
		if self.getRow() + k < 8 and self.getCol() - k > -1 and board[(self.getRow() + k, self.getCol() - k)].getColor() == -self.getColor():
			possible_moves.append((self.getRow() + k, self.getCol() - k))
		l = 1
		while self.getRow() - l > -1 and self.getCol() - l > -1 and board[(self.getRow() - l, self.getCol() - l)].getColor() == 0:
			possible_moves.append((self.getRow() - l, self.getCol() - l))
			l += 1
		if self.getRow() - l > -1 and self.getCol() - l > -1 and board[(self.getRow() - l, self.getCol() - l)].getColor() == -self.getColor():
			possible_moves.append((self.getRow() - l, self.getCol() - l))
		return possible_moves

class Rook(Piece):
	def __init__(self, color, row, col):
		Piece.__init__(self, color, row, col)
		self.type = 'R'
    
	def possible_moves(self, board):
		possible_moves = []
		if not self.isAlive():
			return possible_moves
		i = 1
		while self.getRow() + i < 8 and board[(self.getRow() + i, self.getCol())].getColor() == 0:
			possible_moves.append((self.getRow() + i, self.getCol()))
			i += 1
		if self.getRow() + i < 8 and board[(self.getRow() + i, self.getCol())].getColor() == -self.getColor():
			possible_moves.append((self.getRow() + i, self.getCol()))
		j = 1
		while self.getRow() - j > -1 and board[(self.getRow() - j, self.getCol())].getColor() == 0:
			possible_moves.append((self.getRow() - j, self.getCol()))
			j += 1
		if self.getRow() - j > -1 and board[(self.getRow() - j, self.getCol())].getColor() == -self.getColor():
			possible_moves.append((self.getRow() - j, self.getCol()))
		k = 1
		while self.getCol() + k < 8 and board[(self.getRow(), self.getCol() + k)].getColor() == 0:
			possible_moves.append((self.getRow(), self.getCol() + k))
			k += 1
		if self.getCol() + k < 8 and board[(self.getRow(), self.getCol() + k)].getColor() == -self.getColor():
			possible_moves.append((self.getRow(), self.getCol() + k))   
		l = 1
		while self.getCol() - l > -1 and board[(self.getRow(), self.getCol() - l)].getColor() == 0:
			possible_moves.append((self.getRow(), self.getCol() - l))
			l += 1
		if self.getCol() - l > -1 and board[(self.getRow(), self.getCol() - l)].getColor() == -self.getColor():
			possible_moves.append((self.getRow(), self.getCol() - l)) 
		return possible_moves

class Queen(Piece):
	def __init__(self, color, row, col):
		Piece.__init__(self, color, row, col)
		self.type = 'Q'
    
	def possible_moves(self, board):
		possible_moves = []
		if not self.isAlive():
			return possible_moves
		i = 1
		while self.getRow() + i < 8 and board[(self.getRow() + i, self.getCol())].piece == None:
			possible_moves.append((self.getRow() + i, self.getCol()))
			i += 1
		if self.getRow() + i < 8 and board[(self.getRow() + i, self.getCol())].getColor() == -self.getColor():
			possible_moves.append((self.getRow() + i, self.getCol()))
		j = 1
		while self.getRow() - j > -1 and board[(self.getRow() - j, self.getCol())].piece == None:
			possible_moves.append((self.getRow() - j, self.getCol()))
			j += 1
		if self.getRow() - j > -1 and board[(self.getRow() - j, self.getCol())].getColor() == -self.getColor():
			possible_moves.append((self.getRow() - j, self.getCol()))
		k = 1
		while self.getCol() + k < 8 and board[(self.getRow(), self.getCol() + k)].piece == None:
			possible_moves.append((self.getRow(), self.getCol() + k))
			k += 1
		if self.getCol() + k < 8 and board[(self.getRow(), self.getCol() + k)].getColor() == -self.getColor():
			possible_moves.append((self.getRow(), self.getCol() + k))   
		l = 1
		while self.getCol() - l > -1 and board[(self.getRow(), self.getCol() - l)].piece == None:
			possible_moves.append((self.getRow(), self.getCol() - l))
			l += 1
		if self.getCol() - l > -1 and board[(self.getRow(), self.getCol() - l)].getColor() == -self.getColor():
			possible_moves.append((self.getRow(), self.getCol() - l)) 
		i = 1
		while self.getRow() + i < 8 and self.getCol() + i < 8 and board[(self.getRow() + i, self.getCol() + i)].piece == None:
			possible_moves.append((self.getRow() + i, self.getCol() + i))
			i += 1
		if self.getRow() + i < 8 and self.getCol() + i < 8 and board[(self.getRow() + i, self.getCol() + i)].getColor() == -self.getColor():
			possible_moves.append((self.getRow() + i, self.getCol() + i))
		j = 1
		while self.getRow() - j > -1 and self.getCol() + j < 8 and board[(self.getRow() - j, self.getCol() + j)].piece == None:
			possible_moves.append((self.getRow() - j, self.getCol() + j))
			j += 1
		if self.getRow() - j > -1 and self.getCol() + j < 8 and board[(self.getRow() - j, self.getCol() + j)].getColor() == -self.getColor():
			possible_moves.append((self.getRow() - j, self.getCol() + j))
		k = 1
		while self.getRow() + k < 8 and self.getCol() - k > -1 and board[(self.getRow() + k, self.getCol() - k)].piece == None:
			possible_moves.append((self.getRow() + k, self.getCol() - k))
			k += 1
		if self.getRow() + k < 8 and self.getCol() - k > -1 and board[(self.getRow() + k, self.getCol() - k)].getColor() == -self.getColor():
			possible_moves.append((self.getRow() + k, self.getCol() - k))
		l = 1
		while self.getRow() - l > -1 and self.getCol() - l > -1 and board[(self.getRow() - l, self.getCol() - l)].piece == None:
			possible_moves.append((self.getRow() - l, self.getCol() - l))
			l += 1
		if self.getRow() - l > -1 and self.getCol() - l > -1 and board[(self.getRow() - l, self.getCol() - l)].getColor() == -self.getColor():
			possible_moves.append((self.getRow() - l, self.getCol() - l))
		return possible_moves

class King(Piece):
	def __init__(self, color, row, col):
		Piece.__init__(self, color, row, col)
		self.type = 'K'
    
	def possible_moves(self, board):
		possible_moves = []
		if not self.isAlive():
			return possible_moves
		if self.getRow() + 1 < 8 and self.getCol() + 1 < 8 and board[(self.getRow() + 1, self.getCol() + 1)].getColor() != self.getColor():
			possible_moves.append((self.getRow() + 1, self.getCol() + 1))
		if self.getRow() + 1 < 8 and self.getCol() - 1 > -1 and board[(self.getRow() + 1, self.getCol() - 1)].getColor() != self.getColor():
			possible_moves.append((self.getRow() + 1, self.getCol() - 1))
		if self.getRow() - 1 > -1 and self.getCol() - 1 > -1 and board[(self.getRow() - 1, self.getCol() - 1)].getColor() != self.getColor():
			possible_moves.append((self.getRow() - 1, self.getCol() - 1))
		if self.getRow() - 1 > -1 and self.getCol() + 1 < 8 and board[(self.getRow() - 1, self.getCol() + 1)].getColor() != self.getColor():
			possible_moves.append((self.getRow() - 1, self.getCol() + 1))
		if self.getRow() + 1 < 8 and board[(self.getRow() + 1, self.getCol())].getColor() != self.getColor():
			possible_moves.append((self.getRow() + 1, self.getCol()))
		if self.getRow() - 1 > -1 and board[(self.getRow() - 1, self.getCol())].getColor() != self.getColor():
			possible_moves.append((self.getRow() - 1, self.getCol()))
		if self.getCol() - 1 > -1 and board[(self.getRow(), self.getCol() - 1)].getColor() != self.getColor():
			possible_moves.append((self.getRow(), self.getCol() - 1))
		if self.getCol() + 1 < 8 and board[(self.getRow(), self.getCol() + 1)].getColor() != self.getColor():
			possible_moves.append((self.getRow(), self.getCol() + 1))
		return possible_moves
	
def printBoard(board):
	for i in range(7,-1,-1):
		for j in range(8):
			if board[(i,j)].getColor() == 1:
				print(board[(i,j)].getPiece().getType(), end=" ")
			elif board[(i,j)].getColor() == -1:
				print(board[(i,j)].getPiece().getType().lower(), end=" ")
			else:
				print('*', end=" ")
		print()
		
def move(piece, target, board):
	if piece.getType() == 'P' and target[0] == 3.5 + 3.5 * piece.getColor():
		piece.setPromoted(True)
		if board[target].getPiece() is not None:
			board[target].getPiece().setAlive(False)
		board[(piece.getRow(), piece.getCol())].setPiece(None)
		board[target].setPiece(Queen(piece.getColor(), target[0], target[1]))
		piece.setAlive(False)
	
	else:
		if board[target].getPiece() is not None:
			board[target].getPiece().setAlive(False)
		board[(piece.getRow(), piece.getCol())].setPiece(None)
		piece.setRow(target[0])
		piece.setCol(target[1])
		board[target].setPiece(piece)
		
def isInCheck(color, board):
	for i in range(8):
		for j in range(8):
			if board[(i,j)].getPiece() is not None:
				if board[(i,j)].getPiece().getType() == 'K' and board[(i,j)].getColor() == color:
					row = i
					col = j
					break
				
	for i in range(8):
		for j in range(8):
			if board[(i,j)].getPiece() is not None:
				if board[(i,j)].getPiece().getColor() == -color:
					if (row, col) in board[(i,j)].getPiece().possible_moves(board):
						return True
	return False
	
def generate_legal_moves(piece, board):
	potential_moves = piece.possible_moves(board)
	legal_moves = []
	color = piece.getColor()
	
	for target in potential_moves:
		flag = False
		if board[target].getPiece() is not None:
			flag = True
			replace = board[target].getPiece()
		origRow = piece.getRow()
		origCol = piece.getCol()
		move(piece, target, board)
		if not isInCheck(color, board):
			legal_moves.append(target)
		if piece.getType() == 'P' and piece.getPromoted():
			piece.setAlive(True)
			board[target].setPiece(None)
			piece.setPromoted(False)
			board[(origRow, origCol)].setPiece(piece)
			if flag:
				board[target].setPiece(replace)
				board[target].getPiece().setAlive(True)
			continue
		move(piece, (origRow,origCol), board)
		if flag:
			board[target].setPiece(replace)
			board[target].getPiece().setAlive(True)
	
	return legal_moves
	
def setupBoard():
	board = {}
	for i in range(8):
		for j in range(8):
			board[(i,j)] = Square(i,j)
	#Pawn
	for i in range(8):
		board[(1,i)].setPiece(Pawn(1, 1, i))
		board[(6,i)].setPiece(Pawn(-1, 6, i))
	#Rook
	board[(0,0)].setPiece(Rook(1, 0, 0))
	board[(0,7)].setPiece(Rook(1, 0, 7))
	board[(7,0)].setPiece(Rook(-1, 7, 0))
	board[(7,7)].setPiece(Rook(-1, 7, 7))
	#Knight
	board[(0,1)].setPiece(Knight(1, 0, 1))
	board[(0,6)].setPiece(Knight(1, 0, 6))
	board[(7,1)].setPiece(Knight(-1, 7, 1))
	board[(7,6)].setPiece(Knight(-1, 7, 6))
	#Bishop
	board[(0,2)].setPiece(Bishop(1, 0, 2))
	board[(0,5)].setPiece(Bishop(1, 0, 5))
	board[(7,2)].setPiece(Bishop(-1, 7, 2))
	board[(7,5)].setPiece(Bishop(-1, 7, 5))
	#Queen
	board[(0,3)].setPiece(Queen(1, 0, 3))
	board[(7,3)].setPiece(Queen(-1, 7, 3))
	#King
	board[(0,4)].setPiece(King(1, 0, 4))
	board[(7,4)].setPiece(King(-1, 7, 4))
	return board
	
def findBestMove(color, board):
	bestEval = -999999
	bestMove = (None, None)
	
	for i in range(8):
		for j in range(8):
			if board[(i,j)].getPiece() is None:
				continue
			if board[(i,j)].getColor() == color:
				piece = board[(i,j)].getPiece()
				list = generate_legal_moves(piece, board)
				for target in list:
					flag = False
					if board[target].getPiece() is not None:
						flag = True
						replace = board[target].getPiece()
					origRow = piece.getRow()
					origCol = piece.getCol()
					move(piece, target, board)
					if eval(color, board) > bestEval or random.random() < 2 ** (eval(color, board) - bestEval - 1):
						bestEval = eval(color, board)
						bestMove = (piece, target)
					if piece.getType() == 'P' and piece.getPromoted():
						piece.setAlive(True)
						board[target].setPiece(None)
						piece.setPromoted(False)
						if flag:
							board[target].setPiece(replace)
							board[target].getPiece().setAlive(True)
							continue
					move(piece, (origRow,origCol), board)
					if flag:
						board[target].setPiece(replace)
						board[target].getPiece().setAlive(True)
	return (bestMove, bestEval)
	
def getRandomMove(color, board):
	pieces = 0
	moveList = []
	for i in range(8):
		for j in range(8):
			if board[(i,j)].getPiece() is None:
				continue
			if board[(i,j)].getColor() == color:
				piece = board[(i,j)].getPiece()
				possMoves = generate_legal_moves(piece, board)
				for target in possMoves:
					moveList.append((piece, target))
	choice = random.randint(0, len(moveList)-1)
	return moveList[choice]
				
def eval(color, board):
	whiteMoves, blackMoves = 0, 0
	
	for i in range(8):
		for j in range(8):
			if board[(i,j)].getPiece() is None:
				continue
			if board[(i,j)].getColor() == 1:
				whiteMoves += len(generate_legal_moves(board[(i,j)].getPiece(), board))
			else:
				blackMoves += len(generate_legal_moves(board[(i,j)].getPiece(), board))
	
	return color * ((whiteMoves - blackMoves) + 10 * materialDeficit(board))
	
def materialDeficit(board):
	ret = 0
	value = {}
	value['P'] = 1
	value['N'] = 3
	value['B'] = 3.25
	value['R'] = 5
	value['Q'] = 9
	value['K'] = 1337
	for i in range(8):
		for j in range(8):
			if board[(i,j)].getPiece() is None:
				continue
			ret = ret + board[(i,j)].getPiece().getColor() * value[board[(i,j)].getPiece().getType()]
	return ret
	
'''gameBoard = setupBoard()
i = 1
while True:
	printBoard(gameBoard)
	origRow = int(input())
	origCol = int(input())
	newRow = int(input())
	newCol = int(input())
	move(gameBoard[(origRow, origCol)].getPiece(), (newRow, newCol), gameBoard)
	nextMove = findBestMove(-1, gameBoard)
	if nextMove[0][0] is None:
		break
	move(nextMove[0][0], nextMove[0][1], gameBoard)
	i = i + 1'''

'''gameBoard = setupBoard()
while True:
	nextMove = findBestMove(1, gameBoard)
	if nextMove[0][0] is None:
		break
	move(nextMove[0][0], nextMove[0][1], gameBoard)
	printBoard(gameBoard)
	nextMove = getRandomMove(-1, gameBoard)
	if nextMove[0] is None:
		break
	move(nextMove[0], nextMove[1], gameBoard)
	print()
	printBoard(gameBoard)
	print()'''
	
	
gameBoard = setupBoard()
i = 1	
letters = 'abcdefgh'
while True:
	printBoard(gameBoard)
	print()
	nextMove = findBestMove(2*(i%2)-1, gameBoard)
	if nextMove[0][0] is None:
		break
	if i%2 == 1:
		print(nextMove[0][0].getType(), letters[nextMove[0][0].getCol()], nextMove[0][0].getRow() + 1, '-', letters[nextMove[0][1][1]], nextMove[0][1][0] + 1, ' eval = ', nextMove[1],sep="")
	else:
		print(nextMove[0][0].getType(), letters[nextMove[0][0].getCol()], nextMove[0][0].getRow() + 1, '-', letters[nextMove[0][1][1]], nextMove[0][1][0] + 1, ' eval = ', -nextMove[1],sep="")
	move(nextMove[0][0], nextMove[0][1], gameBoard)
	i = i + 1
