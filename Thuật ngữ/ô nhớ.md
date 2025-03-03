Trong lập trình song song (đặc biệt là trên [[GPU]]), ô (tile) là một khối nhỏ của dữ liệu được xử lý độc lập trong bộ nhớ chia sẻ để tối ưu hiệu suất tính toán.
 Thay vì xử lý toàn bộ dữ liệu cùng lúc, thuật toán chia nhỏ thành các ô để:
 - Tận dụng [[bộ nhớ chia sẻ]] giúp giảm số lần truy cập [[bộ nhớ toàn cục]].
 - Chia nhỏ công việc để các [[khối luồng]] có thể xử lý song song.