public class Chess {
    // Define the chess board as a 2D array
    private static char[][] board = new char[8][8];

    // Initialize the chess board with the starting positions
    public static void initBoard() {
        for (int i = 0; i < 8; i++) {
            for (int j = 0; j < 8; j++) {
                if (i == 1) {
                    board[i][j] = 'P'; // White pawns
                } else if (i == 6) {
                    board[i][j] = 'p'; // Black pawns
                } else if (i == 0) {
                    if (j == 0 || j == 7) {
                        board[i][j] = 'R'; // White rooks
                    } else if (j == 1 || j == 6) {
                        board[i][j] = 'N'; // White knights
                    } else if (j == 2 || j == 5) {
                        board[i][j] = 'B'; // White bishops
                    } else if (j == 3) {
                        board[i][j] = 'Q'; // White queen
                    } else if (j == 4) {
                        board[i][j] = 'K'; // White king
                } else if (i == 7) {
                    if (j == 0 || j == 7) {
                        board[i][j] = 'r'; // Black rooks
                    } else if (j == 1 || j == 6) {
                        board[i][j] = 'n'; // Black knights
                    } else if (j == 2 || j == 5) {
                        board[i][j] = 'b'; // Black bishops
                    } else if (j == 3) {
                        board[i][j] = 'q'; // Black queen
                    } else if (j == 4) {
                        board[i][j] = 'k'; // Black king
                    }
                } else {
                    board[i][j] = '-'; // Empty squares
                }
            }
        }
    }

    // Print the chess board
    public static void printBoard() {
        for (int i = 0; i < 8; i++) {
            for (int j = 0; j < 8; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    // Handle player moves
    public static void makeMove(Scanner scanner) {
        System.out.print("Enter move (e.g., e2-e4): ");
        String move = scanner.nextLine();
        String[] parts = move.split("-");
        int startX = move.charAt(0) - 'a';
        int startY = 8 - (move.charAt(1) - '1');
        int endX = move.charAt(2) - 'a';
        int endY = 8 - (move.charAt(3) - '1');

        // Update the board with the new move
        char piece = board[startY][startX];
        board[startY][startX] = '-';
        board[endY][endX] = piece;
    }

    public static void main(String[] args) {
        initBoard();
        printBoard();

        Scanner scanner = new Scanner(System.in);
        while (true) {
            makeMove(scanner);
            printBoard();
        }
    }
}
