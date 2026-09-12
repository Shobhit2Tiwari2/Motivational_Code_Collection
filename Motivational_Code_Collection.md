# 🚀 Motivational Code Collection

> **A single-file collection of Python, Java, C, and C++ programs that print motivational thoughts to your terminal.**
> Each section is separated by language-specific comments. Copy any block, save with the correct extension, compile/run, and get inspired!

---

## 📌 How to Run Each Code Block

| Language | Save As | Compile & Run |
|----------|---------|---------------|
| Python   | `motivate.py` | `python motivate.py` |
| Java     | `MotivationalEngine.java` | `javac MotivationalEngine.java && java MotivationalEngine` |
| C        | `motivate.c` | `gcc motivate.c -o motivate && ./motivate` |
| C++      | `motivate.cpp` | `g++ -std=c++17 motivate.cpp -o motivate && ./motivate` |

---

<!--
================================================================================
 ██████╗ ██╗   ██╗████████╗██╗  ██╗ ██████╗ ███╗   ██╗
 ██╔══██╗╚██╗ ██╔╝╚══██╔══╝██║  ██║██╔═══██╗████╗  ██║
 ██████╔╝ ╚████╔╝    ██║   ███████║██║   ██║██╔██╗ ██║
 ██╔═══╝   ╚██╔╝     ██║   ██╔══██║██║   ██║██║╚██╗██║
 ██║        ██║      ██║   ██║  ██║╚██████╔╝██║ ╚████║
 ╚═╝        ╚═╝      ╚═╝   ╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═══╝
================================================================================
-->

## 🐍 Python — `motivate.py`

```python
# ==============================================================================
# LANGUAGE: PYTHON
# FILE:     motivate.py
# PURPOSE:  Motivational Thought Engine — Terminal Edition
# RUN:      python motivate.py
# ==============================================================================
# "Code is like humor. When you have to explain it, it's bad." — Cory House
# ==============================================================================

import random
import time
import os
import sys
import datetime
import hashlib
import textwrap
import itertools
import threading

# ==============================================================================
#                        CONFIGURATION & CONSTANTS
# ==============================================================================

PROGRAM_NAME = "Python Motivational Engine"
VERSION = "3.7.1"
AUTHOR = "The Relentless Coder"
BUILD_DATE = "2026-09-12"

# ANSI color codes for terminal styling
class Colors:
    """Terminal color codes for rich output formatting."""
    HEADER    = '\033[95m'
    OKBLUE    = '\033[94m'
    OKCYAN    = '\033[96m'
    OKGREEN   = '\033[92m'
    WARNING   = '\033[93m'
    FAIL      = '\033[91m'
    ENDC      = '\033[0m'
    BOLD      = '\033[1m'
    UNDERLINE = '\033[4m'
    DIM       = '\033[2m'
    ITALIC    = '\033[3m'
    BG_BLACK  = '\033[40m'
    BG_GREEN  = '\033[42m'
    BG_BLUE   = '\033[44m'
    BG_CYAN   = '\033[46m'

# ==============================================================================
#                     MOTIVATIONAL QUOTES DATABASE
# ==============================================================================

MOTIVATIONAL_QUOTES = [
    {
        "quote": "The only way to do great work is to love what you do.",
        "author": "Steve Jobs",
        "category": "passion",
        "year": 2005,
        "context": "Stanford Commencement Speech"
    },
    {
        "quote": "First, solve the problem. Then, write the code.",
        "author": "John Johnson",
        "category": "engineering",
        "year": 2010,
        "context": "Software Engineering Principles"
    },
    {
        "quote": "The best error message is the one that never shows up.",
        "author": "Thomas Fuchs",
        "category": "quality",
        "year": 2013,
        "context": "Web Development Conference"
    },
    {
        "quote": "It's not a bug; it's an undocumented feature.",
        "author": "Anonymous",
        "category": "humor",
        "year": 1990,
        "context": "Developer Folklore"
    },
    {
        "quote": "Believe you can and you're halfway there.",
        "author": "Theodore Roosevelt",
        "category": "mindset",
        "year": 1903,
        "context": "Presidential Address"
    },
    {
        "quote": "Success is not final, failure is not fatal: it is the courage to continue that counts.",
        "author": "Winston Churchill",
        "category": "perseverance",
        "year": 1941,
        "context": "Wartime Speech"
    },
    {
        "quote": "The future belongs to those who believe in the beauty of their dreams.",
        "author": "Eleanor Roosevelt",
        "category": "dreams",
        "year": 1937,
        "context": "Public Address"
    },
    {
        "quote": "Code never lies, comments sometimes do.",
        "author": "Ron Jeffries",
        "category": "engineering",
        "year": 2001,
        "context": "Extreme Programming"
    },
    {
        "quote": "In the middle of every difficulty lies opportunity.",
        "author": "Albert Einstein",
        "category": "opportunity",
        "year": 1940,
        "context": "Personal Correspondence"
    },
    {
        "quote": "Don't watch the clock; do what it does. Keep going.",
        "author": "Sam Levenson",
        "category": "persistence",
        "year": 1972,
        "context": "In One Era & Out the Other"
    },
    {
        "quote": "Programs must be written for people to read, and only incidentally for machines to execute.",
        "author": "Harold Abelson",
        "category": "engineering",
        "year": 1985,
        "context": "Structure and Interpretation of Computer Programs"
    },
    {
        "quote": "The harder you work for something, the greater you'll feel when you achieve it.",
        "author": "Anonymous",
        "category": "effort",
        "year": 2000,
        "context": "Motivational Wisdom"
    },
]

# ==============================================================================
#                        UTILITY FUNCTIONS
# ==============================================================================

def clear_screen():
    """Clear the terminal screen cross-platform."""
    os.system('cls' if os.name == 'nt' else 'clear')


def generate_session_id():
    """Generate a unique session identifier using SHA-256 hashing."""
    timestamp = str(datetime.datetime.now().timestamp())
    random_seed = str(random.randint(100000, 999999))
    raw_string = f"{timestamp}-{random_seed}-{PROGRAM_NAME}"
    session_hash = hashlib.sha256(raw_string.encode('utf-8')).hexdigest()
    return session_hash[:16].upper()


def typewriter_effect(text, delay=0.03):
    """Print text with a typewriter animation effect."""
    for char in text:
        sys.stdout.write(char)
        sys.stdout.flush()
        time.sleep(delay)
    print()


def loading_spinner(message, duration=2):
    """Display an animated loading spinner in the terminal."""
    spinner_chars = itertools.cycle(['⠋', '⠙', '⠹', '⠸', '⠼', '⠴', '⠦', '⠧', '⠇', '⠏'])
    end_time = time.time() + duration
    while time.time() < end_time:
        sys.stdout.write(f'\r  {Colors.OKCYAN}{next(spinner_chars)}{Colors.ENDC} {message}')
        sys.stdout.flush()
        time.sleep(0.1)
    sys.stdout.write('\r' + ' ' * (len(message) + 10) + '\r')
    sys.stdout.flush()


def print_separator(char='═', length=70, color=Colors.DIM):
    """Print a decorative separator line."""
    print(f"{color}{char * length}{Colors.ENDC}")


def print_centered(text, width=70, color=Colors.BOLD):
    """Print text centered within a given width."""
    centered = text.center(width)
    print(f"{color}{centered}{Colors.ENDC}")


def wrap_text(text, width=60, indent="    "):
    """Wrap long text to fit within terminal width."""
    wrapped_lines = textwrap.wrap(text, width=width)
    return '\n'.join(f"{indent}{line}" for line in wrapped_lines)


def get_time_greeting():
    """Return a greeting based on the current time of day."""
    hour = datetime.datetime.now().hour
    if 5 <= hour < 12:
        return "Good Morning", "🌅"
    elif 12 <= hour < 17:
        return "Good Afternoon", "☀️"
    elif 17 <= hour < 21:
        return "Good Evening", "🌆"
    else:
        return "Burning the Midnight Oil", "🌙"


# ==============================================================================
#                     DISPLAY FUNCTIONS
# ==============================================================================

def display_banner():
    """Display the program's ASCII art banner."""
    banner = f"""
{Colors.OKCYAN}{Colors.BOLD}
    ╔══════════════════════════════════════════════════════════════════╗
    ║                                                                  ║
    ║   ██████╗ ██╗   ██╗████████╗██╗  ██╗ ██████╗ ███╗   ██╗        ║
    ║   ██╔══██╗╚██╗ ██╔╝╚══██╔══╝██║  ██║██╔═══██╗████╗  ██║        ║
    ║   ██████╔╝ ╚████╔╝    ██║   ███████║██║   ██║██╔██╗ ██║        ║
    ║   ██╔═══╝   ╚██╔╝     ██║   ██╔══██║██║   ██║██║╚██╗██║        ║
    ║   ██║        ██║      ██║   ██║  ██║╚██████╔╝██║ ╚████║        ║
    ║   ╚═╝        ╚═╝      ╚═╝   ╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═══╝        ║
    ║                                                                  ║
    ║        M O T I V A T I O N A L   E N G I N E   v{VERSION}          ║
    ║                                                                  ║
    ╚══════════════════════════════════════════════════════════════════╝
{Colors.ENDC}"""
    print(banner)


def display_system_info(session_id):
    """Display system and session metadata."""
    now = datetime.datetime.now()
    greeting, emoji = get_time_greeting()

    print(f"\n  {Colors.DIM}┌─────────────────────────────────────────────────────────┐{Colors.ENDC}")
    print(f"  {Colors.DIM}│{Colors.ENDC}  {emoji}  {Colors.BOLD}{greeting}, Developer!{Colors.ENDC}")
    print(f"  {Colors.DIM}│{Colors.ENDC}")
    print(f"  {Colors.DIM}│{Colors.ENDC}  {Colors.OKBLUE}Session ID :{Colors.ENDC}  {session_id}")
    print(f"  {Colors.DIM}│{Colors.ENDC}  {Colors.OKBLUE}Timestamp  :{Colors.ENDC}  {now.strftime('%Y-%m-%d %H:%M:%S')}")
    print(f"  {Colors.DIM}│{Colors.ENDC}  {Colors.OKBLUE}Platform   :{Colors.ENDC}  {sys.platform}")
    print(f"  {Colors.DIM}│{Colors.ENDC}  {Colors.OKBLUE}Python     :{Colors.ENDC}  {sys.version.split()[0]}")
    print(f"  {Colors.DIM}│{Colors.ENDC}  {Colors.OKBLUE}Author     :{Colors.ENDC}  {AUTHOR}")
    print(f"  {Colors.DIM}└─────────────────────────────────────────────────────────┘{Colors.ENDC}")


def display_quote(quote_data, index, total):
    """Display a single motivational quote with full formatting."""
    q = quote_data
    print()
    print_separator('─', 70, Colors.DIM)
    print(f"  {Colors.WARNING}★ Quote {index}/{total}{Colors.ENDC}  {Colors.DIM}[{q['category'].upper()}]{Colors.ENDC}")
    print()
    wrapped = wrap_text(f'"{q["quote"]}"', width=58)
    print(f"{Colors.OKGREEN}{Colors.BOLD}{wrapped}{Colors.ENDC}")
    print()
    print(f"    {Colors.OKCYAN}— {q['author']}{Colors.ENDC}  {Colors.DIM}({q['year']}, {q['context']}){Colors.ENDC}")
    print_separator('─', 70, Colors.DIM)


def display_daily_challenge():
    """Generate and display a random daily coding challenge."""
    challenges = [
        "Write a function that reverses a linked list in-place.",
        "Implement a binary search algorithm from scratch without any library.",
        "Build a simple REST API that returns a random motivational quote.",
        "Create a command-line tool that tracks your daily coding hours.",
        "Write a program that generates Fibonacci numbers using memoization.",
        "Implement a basic LRU cache with O(1) get and put operations.",
        "Build a terminal-based Pomodoro timer for focused coding sessions.",
        "Write a script that analyzes your Git commit history and shows stats.",
    ]
    challenge = random.choice(challenges)
    print(f"\n  {Colors.HEADER}{Colors.BOLD}🎯 TODAY'S CODING CHALLENGE:{Colors.ENDC}")
    print(f"  {Colors.DIM}{'─' * 55}{Colors.ENDC}")
    wrapped = wrap_text(challenge, width=55)
    print(f"{Colors.WARNING}{wrapped}{Colors.ENDC}")
    print(f"  {Colors.DIM}{'─' * 55}{Colors.ENDC}")


def display_progress_bar(current, total, bar_length=40):
    """Display a visual progress bar in the terminal."""
    fraction = current / total
    filled = int(bar_length * fraction)
    bar = '█' * filled + '░' * (bar_length - filled)
    percentage = fraction * 100
    print(f"\r  {Colors.OKGREEN}[{bar}] {percentage:.0f}%{Colors.ENDC}", end='', flush=True)


def display_stats(quotes_shown):
    """Display final session statistics."""
    categories = {}
    for q in quotes_shown:
        cat = q['category']
        categories[cat] = categories.get(cat, 0) + 1

    print(f"\n  {Colors.BOLD}{Colors.OKBLUE}📊 SESSION STATISTICS:{Colors.ENDC}")
    print(f"  {Colors.DIM}{'─' * 45}{Colors.ENDC}")
    print(f"  {Colors.OKCYAN}Total quotes displayed : {len(quotes_shown)}{Colors.ENDC}")
    print(f"  {Colors.OKCYAN}Categories covered     : {len(categories)}{Colors.ENDC}")

    for cat, count in sorted(categories.items()):
        bar = '▓' * (count * 4) + '░' * ((3 - count) * 4)
        print(f"    {Colors.DIM}• {cat.capitalize():20s}{Colors.ENDC} {Colors.OKGREEN}{bar} ({count}){Colors.ENDC}")

    print(f"  {Colors.DIM}{'─' * 45}{Colors.ENDC}")


# ==============================================================================
#                          MAIN EXECUTION
# ==============================================================================

def main():
    """Main program execution — orchestrates the motivational engine."""
    clear_screen()

    # --- PHASE 1: Initialization ---
    session_id = generate_session_id()
    display_banner()

    loading_spinner("Initializing Motivational Engine...", duration=1.5)
    loading_spinner("Loading quote database...", duration=1.0)
    loading_spinner("Calibrating inspiration levels...", duration=0.8)

    display_system_info(session_id)

    # --- PHASE 2: Quote Display ---
    print(f"\n  {Colors.BOLD}{'=' * 60}{Colors.ENDC}")
    print_centered("✨  YOUR DAILY DOSE OF MOTIVATION  ✨", 60, Colors.HEADER + Colors.BOLD)
    print(f"  {Colors.BOLD}{'=' * 60}{Colors.ENDC}")

    selected_quotes = random.sample(MOTIVATIONAL_QUOTES, min(5, len(MOTIVATIONAL_QUOTES)))

    for i, quote in enumerate(selected_quotes, 1):
        display_progress_bar(i, len(selected_quotes))
        time.sleep(0.3)
        display_quote(quote, i, len(selected_quotes))
        time.sleep(0.5)

    # --- PHASE 3: Daily Challenge ---
    display_daily_challenge()

    # --- PHASE 4: Statistics & Sign-off ---
    display_stats(selected_quotes)

    print(f"\n  {Colors.OKGREEN}{Colors.BOLD}{'=' * 60}{Colors.ENDC}")
    print_centered("🔥 Keep Coding. Keep Growing. Keep Believing. 🔥", 60, Colors.OKGREEN + Colors.BOLD)
    print(f"  {Colors.OKGREEN}{Colors.BOLD}{'=' * 60}{Colors.ENDC}")

    print(f"\n  {Colors.DIM}Session {session_id} ended at {datetime.datetime.now().strftime('%H:%M:%S')}{Colors.ENDC}")
    print(f"  {Colors.DIM}Thank you for using {PROGRAM_NAME} v{VERSION}{Colors.ENDC}")
    print(f"\n  {Colors.DIM}Flag1: I_{Colors.ENDC}\n")


if __name__ == "__main__":
    main()
```

---

<!--
================================================================================
      ██╗ █████╗ ██╗   ██╗ █████╗
      ██║██╔══██╗██║   ██║██╔══██╗
      ██║███████║██║   ██║███████║
 ██   ██║██╔══██║╚██╗ ██╔╝██╔══██║
 ╚█████╔╝██║  ██║ ╚████╔╝ ██║  ██║
  ╚════╝ ╚═╝  ╚═╝  ╚═══╝  ╚═╝  ╚═╝
================================================================================
-->

## ☕ Java — `MotivationalEngine.java`

```java
// =============================================================================
// LANGUAGE: JAVA
// FILE:     MotivationalEngine.java
// PURPOSE:  Motivational Thought Engine — Terminal Edition
// RUN:      javac MotivationalEngine.java && java MotivationalEngine
// =============================================================================
// "Java is to JavaScript what car is to carpet." — Chris Heilmann
// =============================================================================

import java.util.*;
import java.time.*;
import java.time.format.DateTimeFormatter;
import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;

/**
 * MotivationalEngine — A comprehensive terminal-based motivational quote
 * display system written in Java. Demonstrates OOP principles, collections,
 * enums, inner classes, formatting, and terminal UI techniques.
 *
 * @author  The Relentless Coder
 * @version 4.2.0
 * @since   2026-09-12
 */
public class MotivationalEngine {

    // =========================================================================
    //                         CONSTANTS & CONFIG
    // =========================================================================

    private static final String PROGRAM_NAME = "Java Motivational Engine";
    private static final String VERSION = "4.2.0";
    private static final String AUTHOR = "The Relentless Coder";
    private static final int DISPLAY_QUOTE_COUNT = 5;
    private static final int SEPARATOR_WIDTH = 65;

    // ANSI escape codes for terminal coloring
    private static final String RESET    = "\033[0m";
    private static final String BOLD     = "\033[1m";
    private static final String DIM      = "\033[2m";
    private static final String ITALIC   = "\033[3m";
    private static final String RED      = "\033[91m";
    private static final String GREEN    = "\033[92m";
    private static final String YELLOW   = "\033[93m";
    private static final String BLUE     = "\033[94m";
    private static final String MAGENTA  = "\033[95m";
    private static final String CYAN     = "\033[96m";
    private static final String WHITE    = "\033[97m";

    // =========================================================================
    //                           ENUMS
    // =========================================================================

    /**
     * Categories for motivational quotes, each with a display emoji.
     */
    enum QuoteCategory {
        PASSION("passion", "🔥"),
        ENGINEERING("engineering", "⚙️"),
        PERSEVERANCE("perseverance", "💪"),
        MINDSET("mindset", "🧠"),
        DREAMS("dreams", "💭"),
        HUMOR("humor", "😄"),
        WISDOM("wisdom", "📚"),
        LEADERSHIP("leadership", "👑"),
        CREATIVITY("creativity", "🎨"),
        GROWTH("growth", "🌱");

        private final String label;
        private final String emoji;

        QuoteCategory(String label, String emoji) {
            this.label = label;
            this.emoji = emoji;
        }

        public String getLabel() { return label; }
        public String getEmoji() { return emoji; }

        @Override
        public String toString() {
            return emoji + " " + label.substring(0, 1).toUpperCase() + label.substring(1);
        }
    }

    // =========================================================================
    //                        INNER CLASSES
    // =========================================================================

    /**
     * Represents a single motivational quote with metadata.
     */
    static class Quote {
        private final String text;
        private final String author;
        private final QuoteCategory category;
        private final int year;
        private final String source;

        public Quote(String text, String author, QuoteCategory category, int year, String source) {
            this.text = text;
            this.author = author;
            this.category = category;
            this.year = year;
            this.source = source;
        }

        public String getText()          { return text; }
        public String getAuthor()        { return author; }
        public QuoteCategory getCategory() { return category; }
        public int getYear()             { return year; }
        public String getSource()        { return source; }

        @Override
        public String toString() {
            return String.format("\"%s\" — %s (%d)", text, author, year);
        }
    }

    /**
     * Session information tracker for the current engine run.
     */
    static class SessionInfo {
        private final String sessionId;
        private final LocalDateTime startTime;
        private final String javaVersion;
        private final String osName;
        private int quotesDisplayed;
        private final Set<QuoteCategory> categoriesCovered;

        public SessionInfo() {
            this.sessionId = generateSessionId();
            this.startTime = LocalDateTime.now();
            this.javaVersion = System.getProperty("java.version");
            this.osName = System.getProperty("os.name");
            this.quotesDisplayed = 0;
            this.categoriesCovered = new HashSet<>();
        }

        private String generateSessionId() {
            try {
                String raw = System.nanoTime() + "-" + Math.random() + "-" + PROGRAM_NAME;
                MessageDigest md = MessageDigest.getInstance("SHA-256");
                byte[] hash = md.digest(raw.getBytes());
                StringBuilder hexString = new StringBuilder();
                for (int i = 0; i < 8; i++) {
                    hexString.append(String.format("%02X", hash[i]));
                }
                return hexString.toString();
            } catch (NoSuchAlgorithmException e) {
                return UUID.randomUUID().toString().substring(0, 16).toUpperCase();
            }
        }

        public void recordQuote(QuoteCategory category) {
            quotesDisplayed++;
            categoriesCovered.add(category);
        }

        public String getSessionId()   { return sessionId; }
        public LocalDateTime getStart() { return startTime; }
        public String getJavaVersion()  { return javaVersion; }
        public String getOsName()       { return osName; }
        public int getQuotesDisplayed() { return quotesDisplayed; }
        public Set<QuoteCategory> getCategoriesCovered() { return categoriesCovered; }
    }

    /**
     * Handles all terminal display formatting and rendering.
     */
    static class TerminalRenderer {

        public static void clearScreen() {
            System.out.print("\033[H\033[2J");
            System.out.flush();
        }

        public static void printSeparator(char ch) {
            String sep = String.valueOf(ch).repeat(SEPARATOR_WIDTH);
            System.out.println("  " + DIM + sep + RESET);
        }

        public static void printCentered(String text) {
            int padding = Math.max(0, (SEPARATOR_WIDTH - text.length()) / 2);
            System.out.println(" ".repeat(padding + 2) + text);
        }

        public static void printBanner() {
            String banner = CYAN + BOLD +
                "\n    ╔═══════════════════════════════════════════════════════════╗\n" +
                "    ║                                                           ║\n" +
                "    ║       ██╗ █████╗ ██╗   ██╗ █████╗                         ║\n" +
                "    ║       ██║██╔══██╗██║   ██║██╔══██╗                        ║\n" +
                "    ║       ██║███████║██║   ██║███████║                        ║\n" +
                "    ║  ██   ██║██╔══██║╚██╗ ██╔╝██╔══██║                       ║\n" +
                "    ║  ╚█████╔╝██║  ██║ ╚████╔╝ ██║  ██║                       ║\n" +
                "    ║   ╚════╝ ╚═╝  ╚═╝  ╚═══╝  ╚═╝  ╚═╝                       ║\n" +
                "    ║                                                           ║\n" +
                "    ║     M O T I V A T I O N A L   E N G I N E   v" + VERSION + "       ║\n" +
                "    ║                                                           ║\n" +
                "    ╚═══════════════════════════════════════════════════════════╝\n" +
                RESET;
            System.out.println(banner);
        }

        public static void printSessionInfo(SessionInfo session) {
            DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
            String greeting = getTimeGreeting();

            System.out.println("\n  " + DIM + "┌─────────────────────────────────────────────────────────┐" + RESET);
            System.out.println("  " + DIM + "│" + RESET + "  " + BOLD + greeting + ", Developer!" + RESET);
            System.out.println("  " + DIM + "│" + RESET);
            System.out.println("  " + DIM + "│" + RESET + "  " + BLUE + "Session ID :" + RESET + "  " + session.getSessionId());
            System.out.println("  " + DIM + "│" + RESET + "  " + BLUE + "Timestamp  :" + RESET + "  " + session.getStart().format(dtf));
            System.out.println("  " + DIM + "│" + RESET + "  " + BLUE + "Platform   :" + RESET + "  " + session.getOsName());
            System.out.println("  " + DIM + "│" + RESET + "  " + BLUE + "Java       :" + RESET + "  " + session.getJavaVersion());
            System.out.println("  " + DIM + "│" + RESET + "  " + BLUE + "Author     :" + RESET + "  " + AUTHOR);
            System.out.println("  " + DIM + "└─────────────────────────────────────────────────────────┘" + RESET);
        }

        private static String getTimeGreeting() {
            int hour = LocalTime.now().getHour();
            if (hour >= 5 && hour < 12)       return "🌅 Good Morning";
            else if (hour >= 12 && hour < 17)  return "☀️ Good Afternoon";
            else if (hour >= 17 && hour < 21)  return "🌆 Good Evening";
            else                               return "🌙 Burning the Midnight Oil";
        }

        public static void printQuote(Quote quote, int index, int total) {
            System.out.println();
            printSeparator('─');
            System.out.println("  " + YELLOW + "★ Quote " + index + "/" + total + RESET +
                             "  " + DIM + "[" + quote.getCategory() + "]" + RESET);
            System.out.println();

            // Word-wrap the quote text
            String wrappedQuote = wrapText("\"" + quote.getText() + "\"", 55);
            for (String line : wrappedQuote.split("\n")) {
                System.out.println("    " + GREEN + BOLD + line + RESET);
            }

            System.out.println();
            System.out.println("    " + CYAN + "— " + quote.getAuthor() + RESET +
                             "  " + DIM + "(" + quote.getYear() + ", " + quote.getSource() + ")" + RESET);
            printSeparator('─');
        }

        public static void printProgressBar(int current, int total) {
            int barLength = 40;
            int filled = (int) ((double) current / total * barLength);
            String bar = "█".repeat(filled) + "░".repeat(barLength - filled);
            int percentage = (int) ((double) current / total * 100);
            System.out.print("\r  " + GREEN + "[" + bar + "] " + percentage + "%" + RESET);
            System.out.flush();
        }

        public static void printStats(SessionInfo session) {
            System.out.println("\n\n  " + BOLD + BLUE + "📊 SESSION STATISTICS:" + RESET);
            printSeparator('─');
            System.out.println("  " + CYAN + "Total quotes displayed : " + session.getQuotesDisplayed() + RESET);
            System.out.println("  " + CYAN + "Categories covered     : " + session.getCategoriesCovered().size() + RESET);

            for (QuoteCategory cat : session.getCategoriesCovered()) {
                System.out.println("    " + DIM + "• " + cat + RESET);
            }
            printSeparator('─');
        }

        public static void printFarewell() {
            System.out.println("\n  " + GREEN + BOLD + "═".repeat(SEPARATOR_WIDTH) + RESET);
            printCentered(GREEN + BOLD + "🔥 Keep Coding. Keep Growing. Keep Believing. 🔥" + RESET);
            System.out.println("  " + GREEN + BOLD + "═".repeat(SEPARATOR_WIDTH) + RESET);
        }

        private static String wrapText(String text, int maxWidth) {
            StringBuilder result = new StringBuilder();
            int index = 0;
            while (index < text.length()) {
                int end = Math.min(index + maxWidth, text.length());
                if (end < text.length() && text.charAt(end) != ' ') {
                    int lastSpace = text.lastIndexOf(' ', end);
                    if (lastSpace > index) {
                        end = lastSpace;
                    }
                }
                result.append(text, index, end).append("\n");
                index = end + (end < text.length() && text.charAt(end) == ' ' ? 1 : 0);
            }
            return result.toString().trim();
        }

        public static void simulateLoading(String message, int durationMs) throws InterruptedException {
            String[] frames = {"⠋", "⠙", "⠹", "⠸", "⠼", "⠴", "⠦", "⠧", "⠇", "⠏"};
            long endTime = System.currentTimeMillis() + durationMs;
            int i = 0;
            while (System.currentTimeMillis() < endTime) {
                System.out.print("\r  " + CYAN + frames[i % frames.length] + RESET + " " + message);
                System.out.flush();
                Thread.sleep(100);
                i++;
            }
            System.out.print("\r" + " ".repeat(message.length() + 10) + "\r");
            System.out.flush();
        }
    }

    // =========================================================================
    //                         QUOTE DATABASE
    // =========================================================================

    private static List<Quote> buildQuoteDatabase() {
        List<Quote> quotes = new ArrayList<>();

        quotes.add(new Quote(
            "The only way to do great work is to love what you do.",
            "Steve Jobs", QuoteCategory.PASSION, 2005, "Stanford Commencement"));

        quotes.add(new Quote(
            "Talk is cheap. Show me the code.",
            "Linus Torvalds", QuoteCategory.ENGINEERING, 2000, "Linux Kernel Mailing List"));

        quotes.add(new Quote(
            "Any fool can write code that a computer can understand. Good programmers write code that humans can understand.",
            "Martin Fowler", QuoteCategory.WISDOM, 1999, "Refactoring"));

        quotes.add(new Quote(
            "Success is not final, failure is not fatal: it is the courage to continue that counts.",
            "Winston Churchill", QuoteCategory.PERSEVERANCE, 1941, "Wartime Address"));

        quotes.add(new Quote(
            "The future belongs to those who believe in the beauty of their dreams.",
            "Eleanor Roosevelt", QuoteCategory.DREAMS, 1937, "Public Address"));

        quotes.add(new Quote(
            "There are only two hard things in computer science: cache invalidation and naming things.",
            "Phil Karlton", QuoteCategory.HUMOR, 1996, "Netscape Engineering"));

        quotes.add(new Quote(
            "Your limitation—it's only your imagination.",
            "Anonymous", QuoteCategory.MINDSET, 2010, "Motivational Wisdom"));

        quotes.add(new Quote(
            "Before software can be reusable, it first has to be usable.",
            "Ralph Johnson", QuoteCategory.ENGINEERING, 1994, "Design Patterns"));

        quotes.add(new Quote(
            "The best time to plant a tree was 20 years ago. The second best time is now.",
            "Chinese Proverb", QuoteCategory.GROWTH, 0, "Ancient Wisdom"));

        quotes.add(new Quote(
            "Innovation distinguishes between a leader and a follower.",
            "Steve Jobs", QuoteCategory.LEADERSHIP, 2001, "Apple Keynote"));

        quotes.add(new Quote(
            "Creativity is intelligence having fun.",
            "Albert Einstein", QuoteCategory.CREATIVITY, 1930, "Personal Letters"));

        quotes.add(new Quote(
            "Code is like humor. When you have to explain it, it's bad.",
            "Cory House", QuoteCategory.HUMOR, 2015, "Twitter"));

        return quotes;
    }

    // =========================================================================
    //                           MAIN
    // =========================================================================

    public static void main(String[] args) throws InterruptedException {
        TerminalRenderer.clearScreen();
        SessionInfo session = new SessionInfo();

        // --- Phase 1: Initialization ---
        TerminalRenderer.printBanner();
        TerminalRenderer.simulateLoading("Initializing Motivational Engine...", 1200);
        TerminalRenderer.simulateLoading("Loading quote database...", 800);
        TerminalRenderer.simulateLoading("Calibrating inspiration levels...", 600);
        TerminalRenderer.printSessionInfo(session);

        // --- Phase 2: Quote Display ---
        List<Quote> allQuotes = buildQuoteDatabase();
        Collections.shuffle(allQuotes);
        List<Quote> selectedQuotes = allQuotes.subList(0, Math.min(DISPLAY_QUOTE_COUNT, allQuotes.size()));

        System.out.println("\n  " + BOLD + "═".repeat(SEPARATOR_WIDTH) + RESET);
        TerminalRenderer.printCentered(MAGENTA + BOLD + "✨  YOUR DAILY DOSE OF MOTIVATION  ✨" + RESET);
        System.out.println("  " + BOLD + "═".repeat(SEPARATOR_WIDTH) + RESET);

        for (int i = 0; i < selectedQuotes.size(); i++) {
            TerminalRenderer.printProgressBar(i + 1, selectedQuotes.size());
            Thread.sleep(300);
            Quote q = selectedQuotes.get(i);
            session.recordQuote(q.getCategory());
            TerminalRenderer.printQuote(q, i + 1, selectedQuotes.size());
            Thread.sleep(400);
        }

        // --- Phase 3: Stats & Sign-off ---
        TerminalRenderer.printStats(session);
        TerminalRenderer.printFarewell();

        DateTimeFormatter dtf = DateTimeFormatter.ofPattern("HH:mm:ss");
        System.out.println("\n  " + DIM + "Session " + session.getSessionId() +
                         " ended at " + LocalTime.now().format(dtf) + RESET);
        System.out.println("  " + DIM + "Thank you for using " + PROGRAM_NAME + " v" + VERSION + RESET);
        System.out.println("\n  " + DIM + "Flag2: Am_" + RESET + "\n");
    }
}
```

---

<!--
================================================================================
  ██████╗
 ██╔════╝
 ██║
 ██║
 ╚██████╗
  ╚═════╝   LANGUAGE
================================================================================
-->

## 🔧 C — `motivate.c`

```c
/* =============================================================================
 * LANGUAGE: C
 * FILE:     motivate.c
 * PURPOSE:  Motivational Thought Engine — Terminal Edition
 * COMPILE:  gcc motivate.c -o motivate
 * RUN:      ./motivate       (Linux/macOS)
 *           motivate.exe     (Windows)
 * =============================================================================
 * "C is quirky, flawed, and an enormous success." — Dennis Ritchie
 * ============================================================================= */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

/* =============================================================================
 *                         CONSTANTS & MACROS
 * ============================================================================= */

#define PROGRAM_NAME       "C Motivational Engine"
#define VERSION            "2.9.0"
#define AUTHOR             "The Relentless Coder"
#define MAX_QUOTES         15
#define MAX_QUOTE_LEN      256
#define MAX_AUTHOR_LEN     64
#define MAX_CATEGORY_LEN   32
#define MAX_SOURCE_LEN     64
#define SEPARATOR_WIDTH    65
#define DISPLAY_COUNT      5

/* ANSI Color Macros */
#define RESET       "\033[0m"
#define BOLD        "\033[1m"
#define DIM         "\033[2m"
#define RED         "\033[91m"
#define GREEN       "\033[92m"
#define YELLOW      "\033[93m"
#define BLUE        "\033[94m"
#define MAGENTA     "\033[95m"
#define CYAN        "\033[96m"
#define WHITE       "\033[97m"

/* =============================================================================
 *                          DATA STRUCTURES
 * ============================================================================= */

/**
 * Represents a single motivational quote entry with metadata.
 */
typedef struct {
    char text[MAX_QUOTE_LEN];
    char author[MAX_AUTHOR_LEN];
    char category[MAX_CATEGORY_LEN];
    int  year;
    char source[MAX_SOURCE_LEN];
} Quote;

/**
 * Holds session-level runtime information.
 */
typedef struct {
    unsigned long session_id;
    time_t        start_time;
    int           quotes_displayed;
    int           categories_seen;
    char          categories_list[MAX_QUOTES][MAX_CATEGORY_LEN];
} SessionInfo;

/* =============================================================================
 *                        FUNCTION PROTOTYPES
 * ============================================================================= */

void        clear_screen(void);
void        print_separator(char ch);
void        print_centered(const char *text);
void        print_banner(void);
void        print_session_info(const SessionInfo *session);
void        print_quote(const Quote *q, int index, int total);
void        print_progress_bar(int current, int total);
void        print_stats(const SessionInfo *session);
void        print_farewell(void);
const char *get_time_greeting(void);
void        simulate_loading(const char *message, int iterations);
int         init_quote_database(Quote quotes[]);
void        shuffle_quotes(Quote quotes[], int n);
void        record_category(SessionInfo *session, const char *category);
void        sleep_ms(int milliseconds);

/* =============================================================================
 *                        UTILITY FUNCTIONS
 * ============================================================================= */

/**
 * Cross-platform screen clearing.
 */
void clear_screen(void) {
    #ifdef _WIN32
        system("cls");
    #else
        system("clear");
    #endif
}

/**
 * Cross-platform millisecond sleep.
 */
void sleep_ms(int milliseconds) {
    /* Simple busy-wait approximation for portability */
    clock_t start = clock();
    while ((clock() - start) * 1000 / CLOCKS_PER_SEC < milliseconds) {
        /* spin */
    }
}

/**
 * Prints a decorative separator line.
 */
void print_separator(char ch) {
    printf("  " DIM);
    for (int i = 0; i < SEPARATOR_WIDTH; i++) {
        putchar(ch);
    }
    printf(RESET "\n");
}

/**
 * Prints text approximately centered within SEPARATOR_WIDTH.
 */
void print_centered(const char *text) {
    int len = (int)strlen(text);
    /* Rough estimate: ANSI codes add ~20 chars of non-visible overhead */
    int visible_len = len > 20 ? len - 20 : len;
    int padding = (SEPARATOR_WIDTH - visible_len) / 2;
    if (padding < 0) padding = 0;
    printf("%*s%s\n", padding + 2, "", text);
}

/**
 * Returns a greeting string based on the current hour.
 */
const char *get_time_greeting(void) {
    time_t now = time(NULL);
    struct tm *t = localtime(&now);
    int hour = t->tm_hour;

    if (hour >= 5 && hour < 12)       return "Good Morning";
    else if (hour >= 12 && hour < 17) return "Good Afternoon";
    else if (hour >= 17 && hour < 21) return "Good Evening";
    else                              return "Burning the Midnight Oil";
}

/**
 * Simple Fisher-Yates shuffle for the quote array.
 */
void shuffle_quotes(Quote quotes[], int n) {
    for (int i = n - 1; i > 0; i--) {
        int j = rand() % (i + 1);
        Quote temp = quotes[i];
        quotes[i] = quotes[j];
        quotes[j] = temp;
    }
}

/**
 * Records a unique category into the session tracker.
 */
void record_category(SessionInfo *session, const char *category) {
    session->quotes_displayed++;
    for (int i = 0; i < session->categories_seen; i++) {
        if (strcmp(session->categories_list[i], category) == 0) {
            return; /* Already recorded */
        }
    }
    strncpy(session->categories_list[session->categories_seen], category, MAX_CATEGORY_LEN - 1);
    session->categories_list[session->categories_seen][MAX_CATEGORY_LEN - 1] = '\0';
    session->categories_seen++;
}

/**
 * Simulates a loading animation.
 */
void simulate_loading(const char *message, int iterations) {
    const char *frames[] = {"/", "-", "\\", "|"};
    int num_frames = 4;
    for (int i = 0; i < iterations; i++) {
        printf("\r  " CYAN "%s" RESET " %s", frames[i % num_frames], message);
        fflush(stdout);
        sleep_ms(120);
    }
    printf("\r%*s\r", (int)(strlen(message) + 10), "");
    fflush(stdout);
}

/* =============================================================================
 *                        DISPLAY FUNCTIONS
 * ============================================================================= */

void print_banner(void) {
    printf(CYAN BOLD "\n");
    printf("    +===========================================================+\n");
    printf("    |                                                           |\n");
    printf("    |        ██████╗                                            |\n");
    printf("    |       ██╔════╝                                            |\n");
    printf("    |       ██║                                                 |\n");
    printf("    |       ██║                                                 |\n");
    printf("    |       ╚██████╗                                            |\n");
    printf("    |        ╚═════╝   LANGUAGE                                 |\n");
    printf("    |                                                           |\n");
    printf("    |    M O T I V A T I O N A L   E N G I N E   v%s       |\n", VERSION);
    printf("    |                                                           |\n");
    printf("    +===========================================================+\n");
    printf(RESET "\n");
}

void print_session_info(const SessionInfo *session) {
    struct tm *t = localtime(&session->start_time);
    char time_buf[32];
    strftime(time_buf, sizeof(time_buf), "%Y-%m-%d %H:%M:%S", t);

    printf("\n  " DIM "+----------------------------------------------------------+" RESET "\n");
    printf("  " DIM "|" RESET "  " BOLD "%s, Developer!" RESET "\n", get_time_greeting());
    printf("  " DIM "|" RESET "\n");
    printf("  " DIM "|" RESET "  " BLUE "Session ID :" RESET "  %08lX\n", session->session_id);
    printf("  " DIM "|" RESET "  " BLUE "Timestamp  :" RESET "  %s\n", time_buf);
    printf("  " DIM "|" RESET "  " BLUE "Compiler   :" RESET "  GCC (C99/C11)\n");
    printf("  " DIM "|" RESET "  " BLUE "Author     :" RESET "  %s\n", AUTHOR);
    printf("  " DIM "+----------------------------------------------------------+" RESET "\n");
}

void print_quote(const Quote *q, int index, int total) {
    printf("\n");
    print_separator('-');
    printf("  " YELLOW "* Quote %d/%d" RESET "  " DIM "[%s]" RESET "\n", index, total, q->category);
    printf("\n");
    printf("    " GREEN BOLD "\"%s\"" RESET "\n", q->text);
    printf("\n");
    printf("    " CYAN "-- %s" RESET "  " DIM "(%d, %s)" RESET "\n", q->author, q->year, q->source);
    print_separator('-');
}

void print_progress_bar(int current, int total) {
    int bar_length = 40;
    int filled = (current * bar_length) / total;
    int percentage = (current * 100) / total;

    printf("\r  " GREEN "[");
    for (int i = 0; i < bar_length; i++) {
        printf("%c", i < filled ? '#' : '.');
    }
    printf("] %d%%" RESET, percentage);
    fflush(stdout);
}

void print_stats(const SessionInfo *session) {
    printf("\n\n  " BOLD BLUE "SESSION STATISTICS:" RESET "\n");
    print_separator('-');
    printf("  " CYAN "Total quotes displayed : %d" RESET "\n", session->quotes_displayed);
    printf("  " CYAN "Categories covered     : %d" RESET "\n", session->categories_seen);
    for (int i = 0; i < session->categories_seen; i++) {
        printf("    " DIM "- %s" RESET "\n", session->categories_list[i]);
    }
    print_separator('-');
}

void print_farewell(void) {
    printf("\n  " GREEN BOLD);
    print_separator('=');
    print_centered(GREEN BOLD ">>> Keep Coding. Keep Growing. Keep Believing. <<<" RESET);
    printf("  " GREEN BOLD);
    print_separator('=');
    printf(RESET);
}

/* =============================================================================
 *                        QUOTE DATABASE
 * ============================================================================= */

int init_quote_database(Quote quotes[]) {
    int count = 0;

    /* Quote 1 */
    strncpy(quotes[count].text, "The only way to learn a new programming language is by writing programs in it.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "Dennis Ritchie", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "ENGINEERING", MAX_CATEGORY_LEN);
    quotes[count].year = 1978;
    strncpy(quotes[count].source, "The C Programming Language", MAX_SOURCE_LEN);
    count++;

    /* Quote 2 */
    strncpy(quotes[count].text, "C is quirky, flawed, and an enormous success.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "Dennis Ritchie", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "WISDOM", MAX_CATEGORY_LEN);
    quotes[count].year = 1993;
    strncpy(quotes[count].source, "ACM Turing Award Lecture", MAX_SOURCE_LEN);
    count++;

    /* Quote 3 */
    strncpy(quotes[count].text, "Believe you can and you're halfway there.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "Theodore Roosevelt", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "MINDSET", MAX_CATEGORY_LEN);
    quotes[count].year = 1903;
    strncpy(quotes[count].source, "Presidential Address", MAX_SOURCE_LEN);
    count++;

    /* Quote 4 */
    strncpy(quotes[count].text, "Success usually comes to those who are too busy to be looking for it.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "Henry David Thoreau", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "PERSEVERANCE", MAX_CATEGORY_LEN);
    quotes[count].year = 1854;
    strncpy(quotes[count].source, "Walden", MAX_SOURCE_LEN);
    count++;

    /* Quote 5 */
    strncpy(quotes[count].text, "In the middle of every difficulty lies opportunity.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "Albert Einstein", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "OPPORTUNITY", MAX_CATEGORY_LEN);
    quotes[count].year = 1940;
    strncpy(quotes[count].source, "Personal Correspondence", MAX_SOURCE_LEN);
    count++;

    /* Quote 6 */
    strncpy(quotes[count].text, "First, solve the problem. Then, write the code.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "John Johnson", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "ENGINEERING", MAX_CATEGORY_LEN);
    quotes[count].year = 2010;
    strncpy(quotes[count].source, "Software Engineering Principles", MAX_SOURCE_LEN);
    count++;

    /* Quote 7 */
    strncpy(quotes[count].text, "Simplicity is the soul of efficiency.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "Austin Freeman", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "WISDOM", MAX_CATEGORY_LEN);
    quotes[count].year = 1920;
    strncpy(quotes[count].source, "The Eye of Osiris", MAX_SOURCE_LEN);
    count++;

    /* Quote 8 */
    strncpy(quotes[count].text, "Don't watch the clock; do what it does. Keep going.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "Sam Levenson", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "PERSISTENCE", MAX_CATEGORY_LEN);
    quotes[count].year = 1972;
    strncpy(quotes[count].source, "In One Era & Out the Other", MAX_SOURCE_LEN);
    count++;

    /* Quote 9 */
    strncpy(quotes[count].text, "Premature optimization is the root of all evil.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "Donald Knuth", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "ENGINEERING", MAX_CATEGORY_LEN);
    quotes[count].year = 1974;
    strncpy(quotes[count].source, "Computer Programming as an Art", MAX_SOURCE_LEN);
    count++;

    /* Quote 10 */
    strncpy(quotes[count].text, "The harder you work for something, the greater you'll feel when you achieve it.", MAX_QUOTE_LEN);
    strncpy(quotes[count].author, "Anonymous", MAX_AUTHOR_LEN);
    strncpy(quotes[count].category, "EFFORT", MAX_CATEGORY_LEN);
    quotes[count].year = 2000;
    strncpy(quotes[count].source, "Motivational Wisdom", MAX_SOURCE_LEN);
    count++;

    return count;
}

/* =============================================================================
 *                            MAIN
 * ============================================================================= */

int main(void) {
    Quote quotes[MAX_QUOTES];
    SessionInfo session;
    int quote_count;
    int display;

    /* Seed random number generator */
    srand((unsigned int)time(NULL));

    /* Initialize session */
    session.session_id = (unsigned long)(rand() % 0xFFFFFF) << 8 | (rand() % 0xFF);
    session.start_time = time(NULL);
    session.quotes_displayed = 0;
    session.categories_seen = 0;

    /* Initialize */
    clear_screen();
    print_banner();

    simulate_loading("Initializing Motivational Engine...", 15);
    simulate_loading("Loading quote database...", 10);
    simulate_loading("Calibrating inspiration levels...", 8);

    /* Load quotes and shuffle */
    quote_count = init_quote_database(quotes);
    shuffle_quotes(quotes, quote_count);

    print_session_info(&session);

    /* Display quotes */
    display = (DISPLAY_COUNT < quote_count) ? DISPLAY_COUNT : quote_count;

    printf("\n  " BOLD);
    print_separator('=');
    print_centered(MAGENTA BOLD ">>>  YOUR DAILY DOSE OF MOTIVATION  <<<" RESET);
    printf("  " BOLD);
    print_separator('=');
    printf(RESET);

    for (int i = 0; i < display; i++) {
        print_progress_bar(i + 1, display);
        sleep_ms(250);
        record_category(&session, quotes[i].category);
        print_quote(&quotes[i], i + 1, display);
        sleep_ms(400);
    }

    /* Stats & farewell */
    print_stats(&session);
    print_farewell();

    {
        struct tm *t = localtime(&session.start_time);
        char end_buf[16];
        time_t now = time(NULL);
        struct tm *end_t = localtime(&now);
        strftime(end_buf, sizeof(end_buf), "%H:%M:%S", end_t);
        printf("\n  " DIM "Session %08lX ended at %s" RESET "\n", session.session_id, end_buf);
    }
    printf("  " DIM "Thank you for using %s v%s" RESET "\n", PROGRAM_NAME, VERSION);
    printf("\n  " DIM "Flag3: The_" RESET "\n\n");

    return 0;
}
```

---

<!--
================================================================================
  ██████╗██╗      ██╗
 ██╔════╝╚██╗    ██╔╝██╗
 ██║      ╚██╗  ██╔╝ ╚═╝
 ██║       ╚██╗██╔╝  ██╗
 ╚██████╗   ╚████╔╝  ╚═╝
  ╚═════╝    ╚═══╝
================================================================================
-->

## ⚡ C++ — `motivate.cpp`

```cpp
// =============================================================================
// LANGUAGE: C++
// FILE:     motivate.cpp
// PURPOSE:  Motivational Thought Engine — Terminal Edition
// COMPILE:  g++ -std=c++17 motivate.cpp -o motivate
// RUN:      ./motivate       (Linux/macOS)
//           motivate.exe     (Windows)
// =============================================================================
// "C++ is designed to allow you to express ideas, but if you don't have
//  ideas or don't have any clue about how to express them, C++ doesn't
//  offer much help." — Bjarne Stroustrup
// =============================================================================

#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
#include <random>
#include <chrono>
#include <thread>
#include <iomanip>
#include <sstream>
#include <functional>
#include <map>
#include <set>
#include <numeric>
#include <ctime>
#include <memory>
#include <optional>

// =============================================================================
//                        NAMESPACE & CONSTANTS
// =============================================================================

namespace motivate {

    constexpr const char* PROGRAM_NAME = "C++ Motivational Engine";
    constexpr const char* VERSION      = "5.1.0";
    constexpr const char* AUTHOR       = "The Relentless Coder";
    constexpr int DISPLAY_COUNT        = 5;
    constexpr int SEPARATOR_WIDTH      = 65;

    // =========================================================================
    //                        ANSI COLOR SYSTEM
    // =========================================================================

    namespace colors {
        constexpr const char* RESET    = "\033[0m";
        constexpr const char* BOLD     = "\033[1m";
        constexpr const char* DIM      = "\033[2m";
        constexpr const char* ITALIC   = "\033[3m";
        constexpr const char* RED      = "\033[91m";
        constexpr const char* GREEN    = "\033[92m";
        constexpr const char* YELLOW   = "\033[93m";
        constexpr const char* BLUE     = "\033[94m";
        constexpr const char* MAGENTA  = "\033[95m";
        constexpr const char* CYAN     = "\033[96m";
        constexpr const char* WHITE    = "\033[97m";

        /**
         * Wraps a string with ANSI color codes.
         */
        inline std::string colorize(const std::string& text, const char* color) {
            return std::string(color) + text + RESET;
        }

        inline std::string bold(const std::string& text) {
            return std::string(BOLD) + text + RESET;
        }

        inline std::string dim(const std::string& text) {
            return std::string(DIM) + text + RESET;
        }
    }

    // =========================================================================
    //                     QUOTE CATEGORY ENUM
    // =========================================================================

    enum class Category {
        Passion,
        Engineering,
        Perseverance,
        Mindset,
        Dreams,
        Humor,
        Wisdom,
        Leadership,
        Creativity,
        Growth,
        Courage,
        Innovation
    };

    /**
     * Returns a string representation of the category with emoji.
     */
    std::string category_to_string(Category cat) {
        static const std::map<Category, std::string> labels = {
            {Category::Passion,      "Passion"},
            {Category::Engineering,  "Engineering"},
            {Category::Perseverance, "Perseverance"},
            {Category::Mindset,      "Mindset"},
            {Category::Dreams,       "Dreams"},
            {Category::Humor,        "Humor"},
            {Category::Wisdom,       "Wisdom"},
            {Category::Leadership,   "Leadership"},
            {Category::Creativity,   "Creativity"},
            {Category::Growth,       "Growth"},
            {Category::Courage,      "Courage"},
            {Category::Innovation,   "Innovation"},
        };
        auto it = labels.find(cat);
        return (it != labels.end()) ? it->second : "Unknown";
    }

    // =========================================================================
    //                         QUOTE CLASS
    // =========================================================================

    /**
     * Represents an immutable motivational quote with metadata.
     */
    class Quote {
    public:
        Quote(std::string text, std::string author, Category category,
              int year, std::string source)
            : text_(std::move(text))
            , author_(std::move(author))
            , category_(category)
            , year_(year)
            , source_(std::move(source))
        {}

        // Getters
        const std::string& text()     const { return text_; }
        const std::string& author()   const { return author_; }
        Category           category() const { return category_; }
        int                year()     const { return year_; }
        const std::string& source()   const { return source_; }

        // Stream insertion operator for easy printing
        friend std::ostream& operator<<(std::ostream& os, const Quote& q) {
            os << "\"" << q.text_ << "\" -- " << q.author_ << " (" << q.year_ << ")";
            return os;
        }

    private:
        std::string text_;
        std::string author_;
        Category    category_;
        int         year_;
        std::string source_;
    };

    // =========================================================================
    //                      SESSION TRACKER CLASS
    // =========================================================================

    /**
     * Tracks runtime session metadata and statistics.
     */
    class SessionTracker {
    public:
        SessionTracker()
            : start_time_(std::chrono::system_clock::now())
            , quotes_displayed_(0)
        {
            session_id_ = generate_session_id();
        }

        void record_quote(Category cat) {
            quotes_displayed_++;
            categories_seen_.insert(cat);
        }

        // Getters
        const std::string& session_id()     const { return session_id_; }
        int quotes_displayed()              const { return quotes_displayed_; }
        const std::set<Category>& categories() const { return categories_seen_; }

        std::string start_time_str() const {
            auto time_t_val = std::chrono::system_clock::to_time_t(start_time_);
            std::stringstream ss;
            ss << std::put_time(std::localtime(&time_t_val), "%Y-%m-%d %H:%M:%S");
            return ss.str();
        }

        std::string current_time_str() const {
            auto now = std::chrono::system_clock::now();
            auto time_t_val = std::chrono::system_clock::to_time_t(now);
            std::stringstream ss;
            ss << std::put_time(std::localtime(&time_t_val), "%H:%M:%S");
            return ss.str();
        }

    private:
        std::string generate_session_id() {
            auto seed = std::chrono::high_resolution_clock::now().time_since_epoch().count();
            std::mt19937_64 gen(seed);
            std::uniform_int_distribution<uint64_t> dist(0, 0xFFFFFFFFFFFFFFFF);
            uint64_t val = dist(gen);

            std::stringstream ss;
            ss << std::uppercase << std::hex << std::setfill('0') << std::setw(16) << val;
            return ss.str().substr(0, 16);
        }

        std::chrono::system_clock::time_point start_time_;
        std::string session_id_;
        int quotes_displayed_;
        std::set<Category> categories_seen_;
    };

    // =========================================================================
    //                    TERMINAL RENDERER CLASS
    // =========================================================================

    /**
     * Handles all terminal output, formatting, and animations.
     */
    class TerminalRenderer {
    public:
        static void clear_screen() {
            std::cout << "\033[H\033[2J";
            std::cout.flush();
        }

        static void print_separator(char ch = '-') {
            std::cout << "  " << colors::DIM;
            for (int i = 0; i < SEPARATOR_WIDTH; ++i) std::cout << ch;
            std::cout << colors::RESET << "\n";
        }

        static void print_centered(const std::string& text) {
            // Rough centering (ignoring ANSI codes length)
            int visible_approx = static_cast<int>(text.size()) - 20;
            if (visible_approx < 0) visible_approx = static_cast<int>(text.size());
            int padding = std::max(0, (SEPARATOR_WIDTH - visible_approx) / 2);
            std::cout << std::string(padding + 2, ' ') << text << "\n";
        }

        static void print_banner() {
            using namespace colors;
            std::cout << CYAN << BOLD << "\n"
                "    +===========================================================+\n"
                "    |                                                           |\n"
                "    |   C++ MOTIVATIONAL ENGINE                                 |\n"
                "    |                                                           |\n"
                "    |    M O T I V A T I O N A L   E N G I N E   v" << VERSION << "        |\n"
                "    |                                                           |\n"
                "    +===========================================================+\n"
                << RESET << "\n";
        }

        static void simulate_loading(const std::string& message, int duration_ms = 1000) {
            const std::vector<std::string> frames = {"/","-","\\","|"};
            auto start = std::chrono::steady_clock::now();
            int i = 0;
            while (true) {
                auto elapsed = std::chrono::steady_clock::now() - start;
                if (std::chrono::duration_cast<std::chrono::milliseconds>(elapsed).count() >= duration_ms)
                    break;

                std::cout << "\r  " << colors::CYAN << frames[i % frames.size()]
                          << colors::RESET << " " << message;
                std::cout.flush();
                std::this_thread::sleep_for(std::chrono::milliseconds(100));
                i++;
            }
            std::cout << "\r" << std::string(message.size() + 10, ' ') << "\r";
            std::cout.flush();
        }

        static void print_session_info(const SessionTracker& session) {
            using namespace colors;
            std::string greeting = get_time_greeting();

            std::cout << "\n  " << DIM << "+----------------------------------------------------------+" << RESET << "\n";
            std::cout << "  " << DIM << "|" << RESET << "  " << BOLD << greeting << ", Developer!" << RESET << "\n";
            std::cout << "  " << DIM << "|" << RESET << "\n";
            std::cout << "  " << DIM << "|" << RESET << "  " << BLUE << "Session ID :" << RESET << "  " << session.session_id() << "\n";
            std::cout << "  " << DIM << "|" << RESET << "  " << BLUE << "Timestamp  :" << RESET << "  " << session.start_time_str() << "\n";
            std::cout << "  " << DIM << "|" << RESET << "  " << BLUE << "Standard   :" << RESET << "  C++17\n";
            std::cout << "  " << DIM << "|" << RESET << "  " << BLUE << "Author     :" << RESET << "  " << AUTHOR << "\n";
            std::cout << "  " << DIM << "+----------------------------------------------------------+" << RESET << "\n";
        }

        static void print_quote(const Quote& q, int index, int total) {
            using namespace colors;
            std::cout << "\n";
            print_separator('-');
            std::cout << "  " << YELLOW << "* Quote " << index << "/" << total << RESET
                      << "  " << DIM << "[" << category_to_string(q.category()) << "]" << RESET << "\n\n";

            // Word wrap the quote
            std::string wrapped = wrap_text("\"" + q.text() + "\"", 55);
            std::istringstream stream(wrapped);
            std::string line;
            while (std::getline(stream, line)) {
                std::cout << "    " << GREEN << BOLD << line << RESET << "\n";
            }

            std::cout << "\n    " << CYAN << "-- " << q.author() << RESET
                      << "  " << DIM << "(" << q.year() << ", " << q.source() << ")" << RESET << "\n";
            print_separator('-');
        }

        static void print_progress_bar(int current, int total) {
            using namespace colors;
            constexpr int bar_length = 40;
            int filled = static_cast<int>(static_cast<double>(current) / total * bar_length);
            int percentage = static_cast<int>(static_cast<double>(current) / total * 100);

            std::cout << "\r  " << GREEN << "[";
            for (int i = 0; i < bar_length; ++i) {
                std::cout << (i < filled ? "#" : ".");
            }
            std::cout << "] " << percentage << "%" << RESET;
            std::cout.flush();
        }

        static void print_stats(const SessionTracker& session) {
            using namespace colors;
            std::cout << "\n\n  " << BOLD << BLUE << "SESSION STATISTICS:" << RESET << "\n";
            print_separator('-');
            std::cout << "  " << CYAN << "Total quotes displayed : " << session.quotes_displayed() << RESET << "\n";
            std::cout << "  " << CYAN << "Categories covered     : " << session.categories().size() << RESET << "\n";

            for (auto cat : session.categories()) {
                std::cout << "    " << DIM << "- " << category_to_string(cat) << RESET << "\n";
            }
            print_separator('-');
        }

        static void print_farewell() {
            using namespace colors;
            std::cout << "\n  " << GREEN << BOLD;
            print_separator('=');
            print_centered(std::string(GREEN) + BOLD + ">>> Keep Coding. Keep Growing. Keep Believing. <<<" + RESET);
            std::cout << "  " << GREEN << BOLD;
            print_separator('=');
            std::cout << RESET;
        }

    private:
        static std::string get_time_greeting() {
            auto now = std::chrono::system_clock::now();
            auto time_t_val = std::chrono::system_clock::to_time_t(now);
            int hour = std::localtime(&time_t_val)->tm_hour;

            if (hour >= 5 && hour < 12)       return "Good Morning";
            else if (hour >= 12 && hour < 17)  return "Good Afternoon";
            else if (hour >= 17 && hour < 21)  return "Good Evening";
            else                               return "Burning the Midnight Oil";
        }

        static std::string wrap_text(const std::string& text, int max_width) {
            std::string result;
            int index = 0;
            int len = static_cast<int>(text.size());

            while (index < len) {
                int end = std::min(index + max_width, len);
                if (end < len && text[end] != ' ') {
                    int last_space = static_cast<int>(text.rfind(' ', end));
                    if (last_space > index) {
                        end = last_space;
                    }
                }
                result += text.substr(index, end - index) + "\n";
                index = end + (end < len && text[end] == ' ' ? 1 : 0);
            }

            // Remove trailing newline
            if (!result.empty() && result.back() == '\n') {
                result.pop_back();
            }
            return result;
        }
    };

    // =========================================================================
    //                        QUOTE DATABASE
    // =========================================================================

    /**
     * Builds and returns the complete motivational quote database.
     */
    std::vector<Quote> build_quote_database() {
        return {
            {"The only way to do great work is to love what you do.",
             "Steve Jobs", Category::Passion, 2005, "Stanford Commencement"},

            {"C++ is designed to allow you to express ideas.",
             "Bjarne Stroustrup", Category::Engineering, 1994, "The Design and Evolution of C++"},

            {"Any fool can write code that a computer can understand. Good programmers write code that humans can understand.",
             "Martin Fowler", Category::Wisdom, 1999, "Refactoring"},

            {"It does not matter how slowly you go as long as you do not stop.",
             "Confucius", Category::Perseverance, -500, "Analects"},

            {"Your limitation -- it's only your imagination.",
             "Anonymous", Category::Mindset, 2010, "Motivational Wisdom"},

            {"The future belongs to those who believe in the beauty of their dreams.",
             "Eleanor Roosevelt", Category::Dreams, 1937, "Public Address"},

            {"A bug is never just a mistake. It represents something bigger. An error of thinking that makes you who you are.",
             "Anonymous", Category::Humor, 2015, "Developer Folklore"},

            {"Creativity is intelligence having fun.",
             "Albert Einstein", Category::Creativity, 1930, "Personal Letters"},

            {"The best time to plant a tree was 20 years ago. The second best time is now.",
             "Chinese Proverb", Category::Growth, 0, "Ancient Wisdom"},

            {"Innovation distinguishes between a leader and a follower.",
             "Steve Jobs", Category::Leadership, 2001, "Apple Keynote"},

            {"Life shrinks or expands in proportion to one's courage.",
             "Anais Nin", Category::Courage, 1969, "The Diary of Anais Nin"},

            {"The measure of intelligence is the ability to change.",
             "Albert Einstein", Category::Innovation, 1935, "Correspondence"},

            {"Talk is cheap. Show me the code.",
             "Linus Torvalds", Category::Engineering, 2000, "LKML"},

            {"Success is not final, failure is not fatal: it is the courage to continue that counts.",
             "Winston Churchill", Category::Perseverance, 1941, "Wartime Address"},
        };
    }

} // namespace motivate

// =============================================================================
//                               MAIN
// =============================================================================

int main() {
    using namespace motivate;
    using namespace motivate::colors;

    TerminalRenderer::clear_screen();
    SessionTracker session;

    // --- Phase 1: Initialization ---
    TerminalRenderer::print_banner();
    TerminalRenderer::simulate_loading("Initializing Motivational Engine...", 1200);
    TerminalRenderer::simulate_loading("Loading quote database...", 800);
    TerminalRenderer::simulate_loading("Calibrating inspiration levels...", 600);
    TerminalRenderer::print_session_info(session);

    // --- Phase 2: Quote Selection & Display ---
    auto quotes = build_quote_database();

    // Shuffle using modern C++ random
    std::random_device rd;
    std::mt19937 gen(rd());
    std::shuffle(quotes.begin(), quotes.end(), gen);

    int count = std::min(DISPLAY_COUNT, static_cast<int>(quotes.size()));

    std::cout << "\n  " << BOLD;
    TerminalRenderer::print_separator('=');
    TerminalRenderer::print_centered(
        std::string(MAGENTA) + BOLD + ">>>  YOUR DAILY DOSE OF MOTIVATION  <<<" + RESET);
    std::cout << "  " << BOLD;
    TerminalRenderer::print_separator('=');
    std::cout << RESET;

    for (int i = 0; i < count; ++i) {
        TerminalRenderer::print_progress_bar(i + 1, count);
        std::this_thread::sleep_for(std::chrono::milliseconds(300));
        session.record_quote(quotes[i].category());
        TerminalRenderer::print_quote(quotes[i], i + 1, count);
        std::this_thread::sleep_for(std::chrono::milliseconds(400));
    }

    // --- Phase 3: Stats & Sign-off ---
    TerminalRenderer::print_stats(session);
    TerminalRenderer::print_farewell();

    std::cout << "\n  " << DIM << "Session " << session.session_id()
              << " ended at " << session.current_time_str() << RESET << "\n";
    std::cout << "  " << DIM << "Thank you for using " << PROGRAM_NAME
              << " v" << VERSION << RESET << "\n";
    std::cout << "\n  " << DIM << "Flag4: Developer" << RESET << "\n\n";

    return 0;
}
```

---

## Quick Start Summary

```bash
# ---- Python ----
# Copy the Python block above into motivate.py, then:
python motivate.py

# ---- Java ----
# Copy the Java block above into MotivationalEngine.java, then:
javac MotivationalEngine.java && java MotivationalEngine

# ---- C ----
# Copy the C block above into motivate.c, then:
gcc motivate.c -o motivate && ./motivate

# ---- C++ ----
# Copy the C++ block above into motivate.cpp, then:
g++ -std=c++17 motivate.cpp -o motivate && ./motivate
```

---

> **Keep Coding. Keep Growing. Keep Believing.**
> *Made with love by The Relentless Coder*
