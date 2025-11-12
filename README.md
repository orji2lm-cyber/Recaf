import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.BorderPane;
import javafx.scene.layout.HBox;
import javafx.scene.paint.Color;
import javafx.scene.shape.Circle;
import javafx.stage.Stage;

public class CircleControl extends Application {

    private Circle circle = new Circle(50);

    @Override
    public void start(Stage primaryStage) {
        circle.setStroke(Color.BLACK);
        circle.setFill(Color.WHITE);

        Button btnEnlarge = new Button("Enlarge");
        Button btnShrink = new Button("Shrink");

        btnEnlarge.setOnAction(e -> circle.setRadius(circle.getRadius() + 2));
        btnShrink.setOnAction(e -> {
            if (circle.getRadius() > 2)
                circle.setRadius(circle.getRadius() - 2);
        });

        HBox hBox = new HBox(10);
        hBox.getChildren().addAll(btnEnlarge, btnShrink);
        hBox.setStyle("-fx-alignment: center; -fx-padding: 10;");

        BorderPane pane = new BorderPane();
        pane.setCenter(circle);
        pane.setBottom(hBox);

        Scene scene = new Scene(pane, 300, 250);
        primaryStage.setTitle("Control Circle");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
